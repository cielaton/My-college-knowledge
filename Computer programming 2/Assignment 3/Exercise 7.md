### Header file for class Ship

```cpp
#include <string>
#include <iostream>

using namespace std;
#ifndef SHIP
#define SHIP

class Ship {
private:
  string name, builtYear;

public:
  Ship() : name(""), builtYear(""){};

  Ship(string shipName, string year) {
    name = shipName;
    builtYear = year;
  };

  void setName(string shipName) { name = shipName; }
  void setBuiltYear(string year) { builtYear = year; }

  string getName() const { return name; }
  string getBuiltYear() const { return builtYear; }

  void print() const {
    cout << "The ship name is: " << name << endl
         << "The year it was built is: " << builtYear;
  }
};

#endif 
```

### Header file for class CruiseShip:

```cpp
#include "header1.h"

#include <iostream>

#ifndef CRUISESHIP
#define CRUISESHIP

class CruiseShip : public Ship {
private:
  int maxPassengers;

public:
  CruiseShip() : maxPassengers(0){};
  CruiseShip(Ship ship, int num) : Ship(ship.getName(), ship.getBuiltYear()) {
    maxPassengers = num;
  }

  void setMaxPassengers(int num) { maxPassengers = num; }

  int getMaxPassengers() const { return maxPassengers; }

  void print() const {
    cout << "The maximum number of passengers is: " << maxPassengers << endl;
  }
};

#endif // !CRUISESHIP
```

### Header file for class CargoShip:

```cpp
#include "header1.h"
#include <iostream>

#ifndef CARGOSHIP
#define CARGOSHIP

class CargoShip : public Ship {
private:
  int capacity;

public:
  CargoShip() : capacity(0){};
  CargoShip(Ship ship, int amount) : Ship(ship.getName(), ship.getBuiltYear()) {
    capacity = amount;
  }

  void setCapacity(int amount) { capacity = amount; }

  int getCapacity() const { return capacity; }

  void print() const { cout << "The cargo capacity is: " << capacity << endl; }
};

#endif
```

### Main file:

```cpp
#include <iostream>

#include "header1.h"
#include "header2.h"
#include "header3.h"

using namespace std;

int main() {
  Ship *arr[3];

  arr[0] = new Ship("Ship 1", "1999");
  arr[1] = new CruiseShip(*arr[0], 20);
  arr[2] = new CargoShip(*arr[0], 10);

  arr[0]->print();
  arr[1]->print();
  arr[2]->print();


  for (int i = 0; i < 3; i++) {
    delete arr[i];
  }
}
```