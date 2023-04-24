#### Class initialization:
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

#### Main program:
```cpp
#include <iostream>

using namespace std;


int main() {
  Employee susan("Susan Meyers", 47899, "Accounting", "Vice President");
  Employee mark("Mark Jones", 39119, "IT", "Programmer");
  Employee joy("Joy Rogers", 81774, "Nanufacturing", "Engineer");

  getInfo(susan);
  getInfo(mark);
  getInfo(joy);
}

```