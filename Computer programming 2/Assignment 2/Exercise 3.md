```cpp
#include <iostream>
#include <string>

using namespace std;

class DayOfYear {
private:
  const string months[14] = {"December", "January",   "Febuary", "March",
                             "April",    "May",       "June",    "July",
                             "August",   "September", "October", "November",
                             "December", "January"};

  const int daysOfMonths[13] = {31, 31, 28, 31, 30, 31, 30,
                                31, 31, 30, 31, 30, 31};

  int modifyDayOfMonth;
  string modifyMonth;

public:
  DayOfYear(int, string);

  void operator++() {
    if (modifyDayOfMonth == 31 || modifyDayOfMonth == 30 ||
        modifyDayOfMonth == 28) {
      modifyDayOfMonth = 1;
      for (int i = 1; i < 13; i++) {
        if (modifyMonth == months[i])
          modifyMonth = months[++i];
      }
    } else
      ++modifyDayOfMonth;
  }
  void operator++(int) {
    if (modifyDayOfMonth == 31 || modifyDayOfMonth == 30 ||
        modifyDayOfMonth == 28) {
      modifyDayOfMonth = 1;
      for (int i = 1; i < 13; i++) {
        if (modifyMonth == months[i])
          modifyMonth = months[++i];
      }
    } else
      modifyDayOfMonth++;
  }

  void operator--() {
    if (modifyDayOfMonth == 1) {
      for (int i = 1; i < 13; i++) {
        if (modifyMonth == months[i]) {
          modifyMonth = months[--i];
          modifyDayOfMonth = daysOfMonths[i];
          break;
        }
      }
    } else
      --modifyDayOfMonth;
  }

  void operator--(int) {
    if (modifyDayOfMonth == 1) {
      for (int i = 1; i < 13; i++) {
        if (modifyMonth == months[i]) {
          modifyMonth = months[--i];
          modifyDayOfMonth = daysOfMonths[i];
          break;
        }
      }
    } else
      modifyDayOfMonth--;
  }

  void print() const;
};

DayOfYear::DayOfYear(int day, string month) {
  for (int i = 1; i < 13; i++) {
    if (month == months[i] && day > 0 && day <= daysOfMonths[i]) {
      modifyDayOfMonth = day;
      modifyMonth = month;
      break;
    }
  }
  if (modifyMonth.empty())
    cout << "The days is out of range for the month or you entered in wrong "
            "format!";
}

void DayOfYear::print() const {
  cout << "The day after modified is: " << modifyMonth << " "
       << modifyDayOfMonth;
};

int main() {
  int inputDay;
  string inputMonth;

  cout << "Please input the month you want to modify (Ex: January): ";
  cin >> inputMonth;

  cout << "Please input the day you want to translate: ";
  cin >> inputDay;

  DayOfYear testingDay = DayOfYear(inputDay, inputMonth);
  --testingDay;
  testingDay.print();
}

```