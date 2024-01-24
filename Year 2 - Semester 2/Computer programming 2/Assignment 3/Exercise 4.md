### Header file
```cpp
#include "header2.h"
#include <iostream>

#ifndef TIMECLOCK_H
#define TIMECLOCK_H

using namespace std;

class TimeClock : public MilTime {
private:
  int startingTime, endingTime;

public:
  TimeClock(int, int);

  int elapsedTime() const;
};

TimeClock::TimeClock(int starting, int ending) : MilTime() {
  startingTime = starting;
  endingTime = ending;
}

int TimeClock::elapsedTime() const { return (startingTime - endingTime) / 100; }
#endif
```

### Main file
```cpp
#include <iostream>

#include "header2.h"
#include "header3.h"

using namespace std;

int main() {
  MilTime time1(1400, 30);
  time1.setTime(1400, 30);
  MilTime time2(1300, 30);
  time2.setTime(1300, 30);

  TimeClock clock(time1.getHours(), time2.getHours());

  cout << "The elapsed time is: " << clock.elapsedTime();
}
```