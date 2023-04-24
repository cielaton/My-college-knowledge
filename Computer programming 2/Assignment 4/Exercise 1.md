#### Header for class Time
```cpp
#ifndef TIME_H
#define TIME_H
class Time {
protected:
  int hour;
  int min;
  int sec;

public:
  // Default constructor
  Time() {
    hour = 0;
    min = 0;
    sec = 0;
  }
  // Constructor
  Time(int h, int m, int s) {
    hour = h;
    min = m;
    sec = s;
  }
  // Accessor functions
  int getHour() const { return hour; }
  int getMin() const { return min; }
  int getSec() const { return sec; }
};
#endif
```

#### Header for class MilTime
```cpp
#include "./header1.h"
#include <iostream>
#include <string>

#ifndef MILTIME
#define MILTIME

using namespace std;

class MilTime : public Time {
private:
  int milHours, milSeconds;

public:
  MilTime(int, int);

  void standardTimeConverter(int, int);

  void setTime(int, int);
  int getHours() const;
  string getStandHr() const;
};

MilTime::MilTime(int hours, int sec) : Time(hours / 100, hours % 100, sec) {
  
  if (hours < 0 || hours > 2359) throw "Error: Bad Hour \n";
  if (sec < 0 || sec > 59) throw "Error: Bad Second\n";

  milHours = hours;
  milSeconds = sec;
}

void MilTime::setTime(int hours, int sec) {
  milHours = hours;
  milSeconds = sec;
}

int MilTime::getHours() const { return milHours; }

string MilTime::getStandHr() const {
  string result;
  if (hour <= 12) {
    result = to_string(hour) + ":" + to_string(min) + "am";
  } else {
    result = to_string(hour - 12) + ":" + to_string(min) + "pm";
  }
  return result;
}
#endif
```

#### Main file
```cpp
#include <iostream>

#include "header2.h"

using namespace std;

int main() {
  int milHours, milSec;

  cout << "Please input the time in military format(ex: 1400 for 2pm): ";
  cin >> milHours;
  cout << endl;

  cout << "Please intput the seccond: ";
  cin >> milSec;
  cout << endl;

  try {
    MilTime testingTime(milHours, milSec);
    cout << "The time in military format: " << testingTime.getHours() << endl
         << "The time in standard format: " << testingTime.getStandHr();
  }

  catch (char const *excetionString) {
    cout << excetionString;
  }
}
```