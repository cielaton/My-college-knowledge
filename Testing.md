```cpp
#ifndef VEHICLE
#define VEHICLE

#include <string>

using namespace std;

class Vehicle {
private:
  int id;
  string name;
  float weight;

public:
  Vehicle(int id, string name, float weight) {
    if (id < 0 || weight < 0 || name.length() == 0) {
      throw "Error: Invalid parameter for Vehicle constructor.";
    }

    this->id = id;
    this->name = name;
    this->weight = weight;
  }

  bool operator==(Vehicle &obj) {
    if (this->weight == obj.weight)
      return true;
    return false;
  }
};

#endif

```

```cpp
#ifndef CAR
#define CAR

#include "vehicle.h"

class Car : public Vehicle {
private:
  int nbSeat;

public:
  void setNbSeat(int nbSeat) { this->nbSeat = nbSeat; 
	  if (nbSeat < 0) throw "A Hùng Ngu";
  }
  int getNbSeat() { return nbSeat; }

	Car (int nbSeat) {};
  Car(int nbSeat, int id, string name, float weight)
      : Vehicle(id, name, weight) {
    if (nbSeat < 0)
      throw "Error: Invalid parameter for Car constructor.";
    this->nbSeat = nbSeat;
  }
};

#endif

```

```cpp
#include "car.h"
#include "vehicle.h"
#include <iostream>

using namespace std;

int main() {

  Vehicle carArr[] = {
      Vehicle(1, "Car1", 1),
      Vehicle(2, "Car2", 2),
      Car(3, 3, "Car3", 3),
  };

  cout << "Vehicle comparison: " << (carArr[0] == carArr[1]) << endl;
}

```

```cpp
#include <iostream>

using namespace std;

template <class T> T interactiveProduct(T arr[], int size) {
  T result = 1;
  for (int i = 0; i < size; i++) {
    result *= arr[i];
  }
  return result;
}

template <class T> T recursiveProduct(T arr[], int size) {
  if (size <= 0) return 0;
  else if (size == 1) 
      return arr[0];
  return arr[size - 1] * recursiveProduct(arr,size - 1);
}



int main() {
  int intArr[] = {1, 2, 3, 4, 5};
  // cout << (sizeof(intArr) / sizeof(int)) - 1;
  double doubleArr[] = {1.1, 2.2, 3.3, 4.4, 5.5};
  // cout << (sizeof(doubleArr) / sizeof(double)) - 1;

  cout << "Interactive: " << endl;
  cout << "intArr: " << interactiveProduct(intArr, sizeof(intArr) / sizeof(int))
       << endl
       << "doubleArr: "
       << interactiveProduct(doubleArr, sizeof(doubleArr) / sizeof(double))
       << endl;

  cout << "recursive: " << endl;
  cout << "intArr: " << recursiveProduct(intArr, (sizeof(intArr) / sizeof(int)))
       << endl
       << "doubleArr: "
       << recursiveProduct(doubleArr, (sizeof(doubleArr) / sizeof(double)))
       << endl;
}
```