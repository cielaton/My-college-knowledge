```cpp
#include <iostream>
#include <string>
using namespace std;

// Class Date
class Date {
  // private members to store date month and year
private:
  int day, month, year;

public:
  // array of string to store months
  string month_names[12] = {"January",   "February", "March",    "April",
                            "May",       "June",     "July",     "August",
                            "September", "October",  "November", "December"};

  // set the values
  void set(int d, int m, int y) {
    day = d;
    month = m;
    year = y;
  }

  // Print functions to print date in Three format
  void print1() {
    cout << month << "/" << day << "/" << year
         << std::endl; // Format Month /day /year
  }

  void print2() {
    cout << month_names[month - 1] << " " << day << ", " << year
         << std::endl; // Format Month name/day/ year
  }

  void print3() {
    cout << day << " " << month_names[month - 1] << " " << year
         << std::endl; // Format Day/month name /year
  }
};

int main() {
  // create an object
  Date date;
  int m, d, y;
  // validate the day
  do {
    cout << "Enter day: ";
    cin >> d;
    if (d < 1 || d > 31) {
      cout << "Invalid day"
           << "try again" << endl;
    }
  } while (d < 1 || d > 31);

  // validate the month
  do {
    cout << "Enter month: ";
    cin >> m;
    if (m < 1 || m > 12) {
      cout << "Invalid month"
           << "try again" << endl;
    }
  } while (m < 1 || m > 12);

  cout << "Enter year: ";
  cin >> y;

  // print the date in three formats
  date.set(d, m, y);
  cout << "\nPrint date in three formats:" << std::endl;
  date.print1();
  cout << endl;
  date.print2();
  cout << endl;
  date.print3();
  return 0;
}
```


Modify the Date class. The new version should have the following overloaded  
operators:  
++ Prefix and postfix increment operators. These operators should increment the object's day member.  
−− Prefix and postfix decrement operators. These operators should decrement the object's day member.  
− Subtraction operator. If one Date object is subtracted from another, the operator should give the number of days between the two dates. For example, if April 10, 2014 is  
subtracted from April 18, 2014, the result will be 8.  
<< cout’s stream insertion operator. This operator should cause the date to be displayed in the form, April 18, 2014  
>> cin’s stream extraction operator. This operator should prompt the user for a date to be stored in a Date object.  

The class should detect the following conditions and handle them accordingly:  
- When a date is set to the last day of the month and incremented, it should become the first day of the following month.  
- When a date is set to December 31 and incremented, it should become January 1 of the following year.  
- When a day is set to the first day of the month and decremented, it should become the last day of the previous month.  
- When a date is set to January 1 and decremented, it should become December 31 of the previous year.  
Demonstrate the class’s capabilities in a simple program.  
Input Validation: The overloaded >> operator should not accept invalid dates. For example, the date 13/45/2014 should not be accepted.

Write the solution for me in cpp

