**Problem 1**: Define class Vehicle having the following members:
- Variables ID (natural number), name (string), weight (kilogram), accessors and mutators for all the variables.
- Constructor accepts some arguments, it throws an exception if one of the following cases happens: ID is negative; weight is negative; name is empty.
- Operator (\=\=) compares two vehicles if their weight are equal.
Define class Car inherits from class Vehicle. It has the following member:
- Variable nbSeats (an integer), accessor and mutator for this variable. Mutator throws an exception if nbSeats is negative.
- Constructor throws an exception if nbSeats is negative.
Write the main function having an array of 10 elements where the two first elements are Vehicle objects and the remaining elements are Car objects. Demonstrate the use of all the functions, constructors and operator defined above.

**Problem 2**: Use template to write the functions to compute the product of all elements in an array. Elements can be real numbers or integers.
a) An iterative version using loop.
b) A recursive version.
Write the main progra to test these function.

---
### Problem 1:
##### Vehicle.h
```cpp
#ifndef VEHICLE
#define VEHICLE

#include <string>
using namespace std;

class Vehicle {
private:
  int ID;
  string name;
  float weight;

public:
  Vehicle();
  Vehicle(int IDVal, string nameVal, float weightVal);
  void setID(int IDVal);
  void setName(string nameVal);
  void setWeight(float weightVal);
  int getID ();
  string getName();
  float getWeight();

  bool operator==(const Vehicle &obj);
};

#endif // !VEHICLE
```
Ở đây chúng ta khai báo class Vehicle như bình thường, với các biến đã được cho trước trong đề. Trong đề có câu "Constructor accepts some arguments" thì có thể viết constructor nhận tất cả tham số cũng được, miễn là có throw exception khi một trong số các tham số đưa vào constructor không đạt yêu cầu. Ngoài ra nên viết thêm constructor mặc định nữa (nên, không bắt buộc). Lưu ý cách khai báo đối với dạng câu operator overloading là phải có keyword **operator**, phải có tham số **const vehicle &obj** để chỉ tham số bên tay phải của toán tử.

##### Vehicle.cpp
```cpp
#include "vehicle.h"

Vehicle::Vehicle() {
  ID = 0;
  name = "";
  weight = 0;
}
Vehicle::Vehicle(int IDVal, string nameVal, float weightVal) {
  if (IDVal < 0 || weightVal < 0 || nameVal == "") {
    throw("Error: The input value is invalid");
  }
  ID = IDVal;
  name = nameVal;
  weight = weightVal;
}

void Vehicle::setID(int IDVal) {
  if (IDVal < 0) {
    throw "Error: The ID value is invalid.";
  }
  ID = IDVal;
}

void Vehicle::setName(string nameVal) {
  if (name == "") {
    throw "Error: The name value is invalid.";
  }
  name = nameVal;
}

void Vehicle::setWeight(float weightVal) {
  if (weight < 0) {
    throw "Error: The weight value is invalid.";
  }
  weight = weightVal;
}

int Vehicle::getID() { return ID; }
string Vehicle::getName() { return name; }
float Vehicle::getWeight() { return weight; }

bool Vehicle::operator==(const Vehicle &obj) {
  return weight == obj.weight;
}

```
- Đối với constructor mặc định, chúng ta gán các giá trị mặc định vào các biến của class.
- Đối với constructor có các tham số, chúng ta đọc yêu cầu đề khi nào thì nên throw ra exception và thực hiện theo. Ở đây anh check chung cho cả 3 tham số luôn, chỉ cần sai 1 trong 3 là sẽ cho ra exception. Nếu
- 