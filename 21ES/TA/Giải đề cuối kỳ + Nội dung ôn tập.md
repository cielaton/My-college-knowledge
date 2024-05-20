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
Ở đây chúng ta khai báo class Vehicle như bình thường, với các biến đã được cho trước trong đề. Trong đề có câu "Constructor accepts some arguments" thì có thể viết constructor nhận tất cả tham số cũng được, miễn là có throw exception khi một trong số các tham số đưa vào constructor không đạt yêu cầu. Ngoài ra nên viết thêm constructor mặc định nữa (thật ra thì cứ viết luôn để khi viết constructor cho class kế thừa nó tiện hơn). Lưu ý cách khai báo đối với dạng câu operator overloading là phải có keyword **operator**, phải có tham số **const vehicle &obj** để chỉ tham số bên tay phải của toán tử.

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
```cpp
Vehicle::Vehicle() {
  ID = 0;
  name = "";
  weight = 0;
}
```
- Đối với constructor có các tham số, chúng ta đọc yêu cầu đề khi nào thì nên throw ra exception và thực hiện theo. Ở đây anh check chung cho cả 3 tham số luôn, chỉ cần sai 1 trong 3 là sẽ cho ra exception. Nếu không lỗi thì gán giá trị vào bình thường.
```cpp
Vehicle::Vehicle(int IDVal, string nameVal, float weightVal) {
  if (IDVal < 0 || weightVal < 0 || nameVal == "") {
    throw("Error: The input value is invalid");
  }
  ID = IDVal;
  name = nameVal;
  weight = weightVal;
}
```
- Đối với các hàm set, cũng throw ra exception mỗi khi tham số truyền vào bị sai yêu cầu.
- Các hàm set thì viết như bình thường.
- Đối với hàm nạp chồng toán tử, vì đề chỉ yêu cầu so sánh khi hai giá trị weight bằng nhau, nên chỉ cần viết return ngắn gọn như sau:
```cpp
bool Vehicle::operator==(const Vehicle &obj) {
  return weight == obj.weight;
}
```
	Lưu ý obj là object phía bên phải khi so sánh.


##### Car.h
```cpp
#ifndef CAR
#define CAR

#include "vehicle.h"

class Car : public Vehicle {
private:
  int nbSeats;

public:
  Car(int seat, int IDVal, string nameVal, float weightVal)
      : Vehicle(IDVal, nameVal, weightVal) {
    if (seat < 0) {
      throw "Error: The seat number is invalid";
    }
    nbSeats = seat;
  }

  void setNbSeats(int seat) ;
  int getNbSeats();
};

#endif // !CAR

```

Class Car được kế thừa từ class Vehicle, và mặc định chúng ta cứ xài luôn kế thừa với keyword là public:
```cpp
class Car : public Vehicle {};
```
Đối với constructor của class Car, mấy đứa có thể không truyền tham số vào Vehicle như kiểu:
```cpp
Car(int seat) {};
```
Khi này constructor mặc định của Vehicle sẽ được gọi để tạo object cho Car.
Còn nếu muốn truyền các tham số cụ thể cho cả Vehicle thông qua Car thì:
```cpp
Car(int seat, int IDVal, string nameVal, float weightVal)
      : Vehicle(IDVal, nameVal, weightVal) {
    if (seat < 0) {
      throw "Error: The seat number is invalid";
    }
    nbSeats = seat;
  }
```
Ở đây các giá trị IDVal, nameVal, weightVal từ Car sẽ được truyền xuống Vehicle, đồng thời check nếu như tham số truyền vào nbSeats bé hơn 0 thì throw exception, nếu không thì gán giá trị vào biến nbSeats.
Viết accessor and mutator cho nbSeats như bình thường.

##### Car.cpp
```cpp
#include "car.h"

void Car::setNbSeats(int seat) {
  if (seat < 0) {
    throw "Error: The seat number is invalid";
  }
  nbSeats = seat;
}

int Car::getNbSeats() { return nbSeats; }

```
Ở đây chỉ lưu ý throw exception nếu tham số truyền vào nbSeats bé hơn 0 khi viết hàm mutator thôi.

##### main.h
```cpp
#include "car.cpp"
#include "vehicle.cpp"
#include <iostream>
using namespace std;

int main() {
  try {
    Vehicle vehicleArr[2] = {Vehicle(2, "name1", 10), Car(5, 1, "name2", 20)};
    cout << "the car name before change: " << vehicleArr[1].getName() << endl;
    vehicleArr[1].setName("nameafterchange");
    cout << "The Car name before change: " << vehicleArr[1].getName() << endl;
    cout << "Is the weight of vehicle 1 equal to the car?: "
         << (vehicleArr[0] == vehicleArr[1]) << endl;
  } catch (char const *msg) {
    cout << msg;
  }
}
```
Ở đây đề kêu viết array của 10 Vehicle nhưng anh lười nên viết 2 thôi, nếu mấy đứa muốn làm như này khi vào thi thì nhớ comment sang bên cạnh kiểu "để tiết kiệm thời gian nên em...", thầy dễ lắm. 
Anh khai báo biến vehicleArr với kiểu dữ liệu là Vehicle, nhưng vì Car kế thừa từ Vehicle nên có thể gán vào mảng này một cách hợp lệ. 
Tiếp theo thì show cách hàm getName, setName và nạp chồng toán tử == hoạt động.
Exception mình throw ra khi khởi tạo object, tức là lúc mình khai báo cái vehicleArr, nên mình nhét nó vào trong block **try**. Sau đó **catch** cái exception được throw ra với tham số là **char const \*mgs**, mấy đứa lưu ý là trong slide thầy không có **const**, nhưng anh compile bị lỗi vì nó báo kiểu dữ liệu khi throw có **const**, mấy đứa vào thi thì skip đoạn này cũng được.

Lưu ý là anh nhét hết tất cả vào trong block **try** bởi vì nếu chỉ nhét mỗi dòng khai báo hàm vào đó thôi, thì khi mình viết như kiểu
```cpp
#include "car.cpp"
#include "vehicle.cpp"
#include <iostream>
using namespace std;

int main() {
  try {
    Vehicle vehicleArr[2] = {Vehicle(2, "name1", 10), Car(5, 1, "name2", 20)};

  } catch (char const *msg) {
    cout << msg;
  }
    cout << "the car name before change: " << vehicleArr[1].getName() << endl;
    vehicleArr[1].setName("nameafterchange");
    cout << "The Car name before change: " << vehicleArr[1].getName() << endl;
    cout << "Is the weight of vehicle 1 equal to the car?: "
         << (vehicleArr[0] == vehicleArr[1]) << endl;
}
```
C++ sẽ không tìm được biến vehicleArr vì nó được khai báo bên trong 1 block (try á), trong khi mình lại gọi nó ra ở ngoài block (nơi nó không tồn tại). Nên lưu ý là không viết kiểu này được nhé cẩn thận kẻo nhầm.

### Problem 2:
```cpp
#include <iostream>

using namespace std;

template <class T> T iterativeProduct(T arr[], int n) {
  T result = 1;
  for (int i = 0; i < n; i++) {
    result *= arr[i];
  }
  return result;
}

template <class T> T recursiveProduct(T arr[], int n) {
  if (n == 0)
    return 1;
  return arr[n - 1] * recursiveProduct(arr, n-1);
}

int main() {
  int arr[5] = {2, 2, 3, 4, 5};
  int n = 5;

  cout << "Iterative: " << iterativeProduct(arr, 5) << endl;
  cout << "Recursive: " << recursiveProduct(arr, 5) << endl;
}

```
Bài này yêu cầu mình viết hàm sử dụng template. Đầu tiên khai báo template theo cú pháp sau, lưu ý là mỗi lần khai báo template chỉ sử dụng được cho 1 hàm thôi, viết hàm sau thì phải khai báo lại.
```cpp
template <class T>
```
Sau đó sử dụng T làm kiểu dữ liệu chung trong lúc định nghĩa hàm.
Chúng ta có hàm tính tích của mảng sử dụng vòng lặp:
```cpp
template <class T> T iterativeProduct(T arr[], int n) {
  T result = 1;
  for (int i = 0; i < n; i++) {
    result *= arr[i];
  }
  return result;
}
```
Truyền vào hàm tham số gồm mảng và độ lớn mảng. Biến result ban đầu là 1, mỗi lần lặp qua mảng thì nhân result với chính giá trị tương ứng của mảng, và cuối cùng là trả về result.

Chúng ta có hàm tính tích của mảng sử dụng đệ quy:
```cpp
template <class T> T recursiveProduct(T arr[], int n) {
  if (n == 0)
    return 1;
  return arr[n - 1] * recursiveProduct(arr, n-1);
}
```
Tham số truyền vào y như cũ, đối với cách đệ quy hoạt động thì mấy đứa có thể tìm hiểu thêm, thậm chí search cái bài tính tích của mảng dùng đệ quy nó cũng ra á, vì giải thích bằng chữ rất khó hình dung nên anh khuyến khích nên google. Hoặc xem cái ví dụ factorial trong slide.
Chúng ta test trong hàm main:
```cpp
int main() {
  int arr[5] = {2, 2, 3, 4, 5};
  int n = 5;

  cout << "Iterative: " << iterativeProduct(arr, 5) << endl;
  cout << "Recursive: " << recursiveProduct(arr, 5) << endl;
}
```
Ở đây có thể khai báo thêm mảng float nữa vì mục đích của template là có thể sử dụng hàm với nhiều kiểu dữ liệu khác nhau.

---
### Một số nội dung cần chú ý khi ôn tập
- Các nội dung cơ bản về Class: Khai báo, Constructor, Destructor, private với public, accessor và mutator, khai báo object, ....
- Static, copy constructor, operator overloading.
- Inheritance (chỉ dùng public), (pure) virtual function, abstract class.
- Exception, template.
- Recursion (có thể ra hoặc không, ôn cho chắc).