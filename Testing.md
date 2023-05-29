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

Write the solution for me in cpp and make sure there is no error.



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

  // Prefix increment operator
  Date operator++() {
    ++day;
    if (day > days_in_month()) {
      day = 1;
      ++month;
      if (month > 12) {
        month = 1;
        ++year;
      }
    }
    return *this;
  }

  // Postfix increment operator
  Date operator++(int) {
    Date temp(*this);
    ++(*this);
    return temp;
  }

  // Prefix decrement operator
  Date operator--() {
    --day;
    if (day < 1) {
      --month;
      if (month < 1) {
        month = 12;
        --year;
      }
      day = days_in_month();
    }
    return *this;
  }

   // Postfix decrement operator
   Date operator--(int)
   {
       Date temp(*this);
       --(*this);
       return temp; 
   }

   // Subtraction operator overload.
   int operator-(const Date& date2)
   {
       int days1 = this->to_days();
       int days2 = date2.to_days();
       return days1 - days2;
   }

   // << operator overload.
   friend ostream& operator<<(ostream& os, const Date& date)
   {
       os << date.month_names[date.month - 1] << " " << date.day << ", " << date.year;
       return os;
   }

   // >> operator overload.
   friend istream& operator>>(istream& is, Date& date)
   {
       int d, m, y;
       char c1, c2;
       is >> m >> c1 >> d >> c2 >> y;

       if (is.fail() || c1 != '/' || c2 != '/' || d < 1 || d > 31 || m < 1 || m > 12) {
           is.setstate(ios_base::failbit);
           return is;
        }
       
        date.set(d, m, y);
        return is;
    }

    // Function to calculate number of days in a month
    int days_in_month() const
    {
        if (month == 2) {
            if ((year % 4 == 0 && year % 100 != 0) || year % 400 == 0) {
                return 29;
            } else {
                return 28;
            }
        } else if (month == 4 || month == 6 || month ==9|| month==11) {
            return 30;
        } else {
            return 31; 
        }
    }

    // Function to convert date to number of days since January first of year zero
    int to_days() const
    {
        int total_days = day -1; 
        for(int i=1;i<month;i++)
        {
             Date temp_date = *this; 
             temp_date.month = i; 
             total_days += temp_date.days_in_month();
         }
         
         for(int i=0;i<year;i++)
         {
             Date temp_date = *this; 
             temp_date.year = i; 
             if((i % 4 == 0 && i % 100 !=0) || i % 400 ==0)
             {
                 total_days += 366;
             }
             else
             {
                 total_days +=365;
             }
         }
         return total_days; 
    }
};

int main() {
  // create an object
  Date date;
  
  // Demonstrate the prefix and postfix increment and decrement operators.
  cout << "Demonstrating prefix and postfix increment and decrement operators:" << endl;
  date.set(31,12,2019);
  cout << "Original date: " << date << endl;
  
  ++date;
  cout << "After prefix increment: " << date << endl;
  
  date++;
  cout << "After postfix increment: " << date << endl;

  --date;
   cout << "After prefix decrement: " << date << endl;

   date--;
   cout<< "After postfix decrement: "<<date<<endl;

   // Demonstrate the subtraction operator.
   cout<<"\nDemonstrating subtraction operator:"<<endl;

   Date d1, d2; 

   d1.set(10,4,2014);
   d2.set(18,4,2014);

   int days = d2 - d1;

   cout<<d2<<" - "<<d1<<" = "<<days<<" days"<<endl;

   // Demonstrate the >> operator overload.
    cout<<"\nDemonstrating >> operator overload:"<<endl;

    Date input_date; 
    do{
        cout<<"Enter a valid date (m/d/y): ";
        cin>>input_date; 
        if(cin.fail())
        {
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(),'\n');
            cout<<"Invalid date. Try again."<<endl;
        }
    }while(cin.fail());
    cout<<"You entered: "<<input_date<<endl;
    return 0;
}
```
