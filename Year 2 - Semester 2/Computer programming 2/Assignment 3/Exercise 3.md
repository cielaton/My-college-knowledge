### Header file
```cpp
#include "Time.h"
#include <iostream>
#include <string>

#ifndef TIME_H
#define TIME_H

using namespace std;

class MilTime : public Time {
private:
  int milHours, milSeconds;

public:
  void standardTimeConverter(int, int);

  MilTime(int, int);

  void setTime(int, int);

  int getHours() const;
  string getStandHr() const;
};

MilTime::MilTime(int hours, int sec) : Time(hours / 100, hours % 100, sec) {}

void MilTime::jsetTime(int hours, int sec) {
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

### Main file
```cpp
#include <iostream>

#include "header2.h"

using namespace std;

int main() {
  int milHours, milSec;

  cout << "Please input the time in military format(ex: 1400 for 2pm): ";
  while (true) {
    cin >> milHours;
    cout << endl;

    if (milHours >= 0 || milHours <= 2359) {
      break;
    } else
      cout << "Your input is not valid, please enter again.";
  }

  cout << "Please intput the seccond: ";
  while (true) {
    cin >> milSec;
    cout << endl;

    if (milSec >= 0 || milSec <= 59) {
      break;
    } else
      cout << "Your input is not valid, please enter again.";
  }

  MilTime testingTime(milHours, milSec);
  testingTime.setTime(milHours, milSec);

  cout << "The time in military format: " << testingTime.getHours() << endl
       << "The time in standard format: " << testingTime.getStandHr();
}
```