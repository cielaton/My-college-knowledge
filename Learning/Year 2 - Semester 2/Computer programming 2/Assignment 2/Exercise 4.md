```cpp
#include <iostream>
#include <string>

using namespace std;

class NumDays {
private:
  int workHours;
  float days;

public:
  NumDays() : workHours(0){};
  NumDays(int);

  void convertToDays() { days = workHours / 8; }

  void setWorkHours(int);
  void setDays(float);

  int getWorkHours() const;
  float getDays() const;

  NumDays operator+(NumDays obj) {
    NumDays temp;
    temp.workHours = workHours + obj.workHours;
    temp.days = days + obj.days;
    return temp;
  }

  NumDays operator-(NumDays obj) {
    NumDays temp;
    temp.workHours = workHours - obj.workHours;
    temp.days = days - obj.days;
    return temp;
  }

  void operator++() {
    ++workHours;
    convertToDays();
  }

  void operator++(int) {
    workHours++;
    convertToDays();
  }

  void operator--() {
    --workHours;
    convertToDays();
  }
  void operator--(int) {
    workHours--;
    convertToDays();
  }
};

NumDays::NumDays(int hours) {
  workHours = hours;
  convertToDays();
}

void NumDays::setWorkHours(int hours) { workHours = hours; }
void NumDays::setDays(float days) { days = days; }

int NumDays::getWorkHours() const { return workHours; }
float NumDays::getDays() const { return days; }

int main() {
  NumDays test1(8), test2(12), test3;
  test3 = test1 + test2;

  cout << test3.getWorkHours() << "\n" << test3.getDays();
}
```