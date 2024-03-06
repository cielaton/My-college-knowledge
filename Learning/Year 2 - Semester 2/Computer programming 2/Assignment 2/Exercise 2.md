```cpp
#include <iostream>
#include <string>

using namespace std;

class DayOfYear {
private:
  int day;

  const string months[13] = {
      "",     "January", "Febuary",   "March",   "April",    "May",     "June",
      "July", "August",  "September", "October", "November", "December"};

  const int daysOfMonths[13] = {0,  31, 28, 31, 30, 31, 30,
                                31, 31, 30, 31, 30, 31};

public:
  DayOfYear(int);
  int getDay() const { return day; }
  void print() const;
};

DayOfYear::DayOfYear(int num) { day = num; }

void DayOfYear::print() const {
  int calculatedDay = getDay();
  for (int i = 1; i <= 13; i++) {
    if (calculatedDay <= 0) {
      cout << months[i - 1] << " " << calculatedDay + daysOfMonths[i - 1];
      break;
   }
    calculatedDay -= daysOfMonths[i];
  }
};
int main() {
  int inputNum;

  cout << "Please input the day you want to translate: ";
  cin >> inputNum;

  DayOfYear testingDay = DayOfYear(inputNum);
  testingDay.print();
}

```