The Employee class:
```cpp
#include <string>

class Employee {
private:
  string name;
  int idNumber;
  string department;
  string position;

public:
  Employee();
  Employee(string, int);
  Employee(string, int, string, string);

  void setName(string);
  void setIdNumber(int);
  void setDepartment(string);
  void setPosition(string);

  string getName() const;
  int getIdNumber() const;
  string getDepartment() const;
  string getPosition() const;
};

Employee::Employee() {
  name = "";
  idNumber = 0;
  department = "";
  position = "";
}

Employee::Employee(string name, int id) {
  name = name;
  idNumber = id;
  department = "";
  position = "";
}

void Employee::setName(string name) { name = name; }
void Employee::setIdNumber(int id) { idNumber = id; }
void Employee::setDepartment(string dep) { department = dep; }
void Employee::setPosition(string pos) { position = pos; }

string Employee::getName() const { return name; };
int Employee::getIdNumber() const { return idNumber; };
string Employee::getDepartment() const { return department; };
string Employee::getPosition() const { return position; };

void getInfo(Employee instance) {
  cout << instance.getName() << " info:\n"
       << "ID Number: " << instance.getIdNumber() << endl
       << "Department: " << instance.getDepartment() << endl
       << "Position: " << instance.getPosition() << endl;
}
```

In a particular factory a shift supervisor is a salaried employee who supervises a shift. In addition to a salary, the shift supervisor earns a yearly bonus when his or her shift meets production goals. Design a ShiftSupervisor class that is derived from the Employee class you created. The ShiftSupervisor class should have a member variable that holds the annual salary and a member variable that holds the annual production bonus that a shift supervisor has earned. Write one or more constructors and the appropriate accessor and mutator functions for the class. Demonstrate the class by writing a program that uses a ShiftSupervisor object.

Write the solution for the above problem in cpp and make sure there is no error.



```cpp
#include <iostream>
#include <string>

using namespace std;

class Employee {
private:
  string name;
  int idNumber;
  string department;
  string position;

public:
  Employee();
  Employee(string, int);
  Employee(string, int, string, string);

  void setName(string);
  void setIdNumber(int);
  void setDepartment(string);
  void setPosition(string);

  string getName() const;
  int getIdNumber() const;
  string getDepartment() const;
  string getPosition() const;
};

Employee::Employee() {
  name = "";
  idNumber = 0;
  department = "";
  position = "";
}

Employee::Employee(string name, int id) {
  this->name = name; // using "this" pointer to avoid naming conflict
  idNumber = id;
}

Employee::Employee(string name, int id, string dep, string pos) {
    this->name = name;
    idNumber = id;
    department = dep;
    position = pos;
}

void Employee::setName(string name) { this->name = name; }
void Employee::setIdNumber(int id) { idNumber = id; }
void Employee::setDepartment(string dep) { department = dep; }
void Employee::setPosition(string pos) { position = pos; }

string Employee::getName() const { return name; };
int Employee::getIdNumber() const { return idNumber; };
string Employee::getDepartment() const { return department; };
string Employee::getPosition() const { return position; };

class ShiftSupervisor : public Employee {
private:
    double annualSalary;
    double annualProductionBonus;

public:
    ShiftSupervisor();
    ShiftSupervisor(double salary, double bonus);
    
    void setAnnualSalary(double salary);
    void setAnnualProductionBonus(double bonus);
    
    double getAnnualSalary();
    double getAnnualProductionBonus();
};

ShiftSupervisor::ShiftSupervisor() {
    annualSalary = 0;
    annualProductionBonus = 0;
}

ShiftSupervisor::ShiftSupervisor(double salary, double bonus) {
    annualSalary = salary;
    annualProductionBonus = bonus;
}

void ShiftSupervisor::setAnnualSalary(double salary) { annualSalary = salary; }
void ShiftSupervisor::setAnnualProductionBonus(double bonus) { annualProductionBonus = bonus; }

double ShiftSupervisor::getAnnualSalary() { return annualSalary; }
double ShiftSupervisor::getAnnualProductionBonus() { return annualProductionBonus; }

int main() {
    ShiftSupervisor supervisor(50000, 10000);
    
    supervisor.setName("John Doe");
    supervisor.setIdNumber(12345);
    supervisor.setDepartment("Manufacturing");
    supervisor.setPosition("Shift Supervisor");

    cout << "Name: " << supervisor.getName() << endl
         << "ID Number: " << supervisor.getIdNumber() << endl
         << "Department: " << supervisor.getDepartment() << endl
         << "Position: " << supervisor.getPosition() << endl
         << "Annual Salary: $" << supervisor.getAnnualSalary() << endl
         << "Annual Production Bonus: $" << supervisor.getAnnualProductionBonus() 
         << endl;

    return 0;
}
```