```cpp
#include <iostream>

using namespace std;

class Month {
private:
  string monthList[13] = {
      "",     "January", "Febuary",   "March",   "April",    "May",     "June",
      "July", "August",  "September", "October", "November", "December"};

  string name;
  int monthNumber;

public:
  Month(string name = "January", int monthNumber = 1);
  Month(string);
  Month(int);

  void setName(string);
  void setMonthNumber(int);

  string getName();
  int getMonthNumber();

  Month operator++() {
    Month temp;
    if (monthNumber == 12) {
      temp.monthNumber = 1;
      temp.name = monthList[1];
    } else {
      temp.monthNumber = ++monthNumber;
      temp.name = monthList[temp.monthNumber];
    }

    return temp;
  }

  Month operator++(int) {
    Month temp;

    if (monthNumber == 12) {
      monthNumber = 1;
      name = monthList[1];
    } else {
      temp.monthNumber = monthNumber++;
      temp.name = monthList[temp.monthNumber];
    }

    name = monthList[monthNumber];
    return temp;
  }

  Month operator--() {
    Month temp;

    if (monthNumber == 1) {
      temp.monthNumber = 12;
      temp.name = monthList[12];
    } else {
      temp.monthNumber = --monthNumber;
      temp.name = monthList[temp.monthNumber];
    }
    return temp;
  }

  Month operator--(int);

  friend ostream &operator<<(ostream &os, Month monthObj);
  friend istream &operator>>(istream &in, Month monthObj);
};

ostream &operator<<(ostream &os, Month monthObj) {
  os << "The month number: " << monthObj.monthNumber << endl
     << "The month name: " << monthObj.name;
  return os;
}
istream &operator>>(istream &in, Month monthObj) {
  cout << "Enter the month number: ";
  in >> monthObj.monthNumber;
  cout << endl << "Enter the month name: ";
  in >> monthObj.name;
  return in;
}

Month::Month(string month) {
  for (int i = 1; i < 13; i++) {
    if (month == monthList[i]) {
      name = month;
      monthNumber = i;
    }
  }
  if (month.length() == 0)
    cout << "The month name is in wrong format!";
}

Month::Month(int monthNum) {
  if (monthNum <= 1 && monthNum > 12) {
    cout << "The month name is in wrong format!";
  }
  monthNumber = monthNum;
  name = monthList[monthNum];
}

```