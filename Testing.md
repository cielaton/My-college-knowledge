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

