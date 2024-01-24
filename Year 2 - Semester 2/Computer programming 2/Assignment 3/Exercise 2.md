### Header file
```cpp
#include "./header1.h"
#ifndef TIME_H
#define TIME_H

class TeamLeader : public ProductionWorker {
private:
  double monthlyBonusAmount;
  int requiredTrainingHours, attendedTrainingHours;

public:
  TeamLeader(string, int, string, int, double, double, int, int);

  void setMonthlyBonusAmount(double);
  void setRequiredTrainingHours(int);
  void setAttendedTrainingHours(int);

  double getMonthlyBonusAmount() const;
  int getRequiredTrainingHours() const;
  int getAttendedTrainingHours() const;
};

TeamLeader::TeamLeader(string employeeName, int employeeNum, string date,
                       int workShift, double rate, double bonusAmount,
                       int requiredHours, int attendedHours)
    : ProductionWorker(employeeName, employeeNum, date, workShift, rate) {
  monthlyBonusAmount = bonusAmount;
  requiredTrainingHours = requiredHours;
  attendedTrainingHours = attendedHours;
}

void TeamLeader::setMonthlyBonusAmount(double bonusAmount) {
  monthlyBonusAmount = bonusAmount;
}
void TeamLeader::setRequiredTrainingHours(int requiredHours) {
  requiredTrainingHours = requiredHours;
}
void TeamLeader::setAttendedTrainingHours(int attendedHours) {
  attendedTrainingHours = attendedHours;
}

double TeamLeader::getMonthlyBonusAmount() const { return monthlyBonusAmount; }
int TeamLeader::getRequiredTrainingHours() const {
  return requiredTrainingHours;
}
int TeamLeader::getAttendedTrainingHours() const {
  return attendedTrainingHours;
}
#endif
```

### Main file
```cpp
#include <iostream>

#include "./header2.h"

using namespace std;

int main() {
  string workerName, date;
  int workerNumber, shift, requiredHours, attendedHours;
  double rate, bonusAmount;

  cout << "Please input a worker name: ";
  cin >> workerName;
  cout << endl;

  cout << "Please input a worker number: ";
  cin >> workerNumber;
  cout << endl;

  cout << "PLease input the hired day: ";
  cin >> date;
  cout << endl;

  cout << "Please input the shift (number 1 for day, number 2 for night): ";
  while (true) {
    cin >> shift;
    if (shift == 1 || shift == 2) {
      break;
    } else 
	  cout << "Your input value must be 1 or 2";
  }

  cout << "Please input the hourly pay rate: ";
  cin >> rate;
  cout << endl;

  cout << "Please input the monthly bonus amount: ";
  cin >> bonusAmount;
  cout << endl;

  cout << "Please input the required training hours: ";
  cin >> requiredHours;
  cout << endl;

  cout << "Please input the attended training hours: ";
  cin >> attendedHours;
  cout << endl;

  TeamLeader worker1(workerName, workerNumber, date, shift, rate, bonusAmount,
                     requiredHours, attendedHours);

  cout << worker1.getName();
}
```