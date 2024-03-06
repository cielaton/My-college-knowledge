### Header file
```cpp
#include <string>
#ifndef TIME_H
#define TIME_H
using namespace std;

class Employee {
private:
  string name;
  int number;
  string hiredDate;

public:
  Employee(string, int, string);

  void setName(string);
  void setNumber(int);
  void setHiredDate(string);

  string getName() const;
  int getNumber() const;
  string getHiredDate() const;
};

Employee::Employee(string employeeName, int employeeNum, string date) {
  name = employeeName;
  number = employeeNum;
  hiredDate = date;
}

void Employee::setName(string employeeName) { name = employeeName; }
void Employee::setNumber(int employeeNum) { number = employeeNum; }
void Employee::setHiredDate(string date) { hiredDate = date; }

string Employee::getName() const { return name; }
int Employee::getNumber() const { return number; }
string Employee::getHiredDate() const { return hiredDate; }

class ProductionWorker : public Employee {
private:
  int shift;
  double hourlyPayRate;

public:
  ProductionWorker(string, int, string, int, double);

  void setShift(int);
  void setHourlyPayRate(double);

  int getShift() const;
  double getHourlyPayRate() const;
};

ProductionWorker::ProductionWorker(string employeeName, int employeeNum,
                                   string date, int workShift, double rate)
    : Employee(employeeName, employeeNum, date) {
  shift = workShift;
  hourlyPayRate = rate;
};

void ProductionWorker::setShift(int workShift) { shift = workShift; }
void ProductionWorker::setHourlyPayRate(double rate) { hourlyPayRate = rate; }

int ProductionWorker::getShift() const { return shift; }
double ProductionWorker::getHourlyPayRate() const { return hourlyPayRate; }
#endif
```

### Main file
```cpp
#include <iostream>
#include "./header1.h"

using namespace std;

int main() {
  string workerName, date;
  int workerNumber, shift;
  double rate;

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
    }
  }

  cout << "Please input the hourly pay rate: ";
  cin >> rate;
  cout << endl;

  ProductionWorker worker1(workerName, workerNumber, date, shift, rate);

  cout << worker1.getName();
}
```