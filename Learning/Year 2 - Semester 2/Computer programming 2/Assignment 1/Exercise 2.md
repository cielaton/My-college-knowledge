#### Class initialization:
```cpp
#include <string>
class Car {
private:
  int yearModel;
  string make;
  int speed;

public:
  Car(int);

  void setYearModel(int);
  void setMake(string);
  void setSpeed(int);

  int getYearModel() const;
  string getMake() const;
  int getSpeed() const;

  void accelerate() { speed += 5; }
  void brake() { speed -= 5; }
};

Car ::Car(int year) {
  yearModel = year;
  speed = 0;
}

void Car::setYearModel(int year) { yearModel = year; };
void Car::setSpeed(int speed) { speed = speed; };
void Car::setMake(string make) { make = make; };

int Car::getYearModel() const { return yearModel; };
string Car::getMake() const { return make; };
int Car::getSpeed() const { return speed; };

```

#### Main program
```cpp
#include <iostream>

using namespace std;

int main() {
  Car testCar(2000);

  testCar.accelerate();
  cout << "Current speed of the car is: " << testCar.getSpeed();
  testCar.accelerate();
  cout << "Current speed of the car is: " << testCar.getSpeed();
  testCar.accelerate();
  cout << "Current speed of the car is: " << testCar.getSpeed();
  testCar.accelerate();
  cout << "Current speed of the car is: " << testCar.getSpeed();
  testCar.accelerate();
  cout << "Current speed of the car is: " << testCar.getSpeed();

  testCar.brake();
  cout << "Current speed of the car is: " << testCar.getSpeed();
  testCar.brake();
  cout << "Current speed of the car is: " << testCar.getSpeed();
  testCar.brake();
  cout << "Current speed of the car is: " << testCar.getSpeed();
  testCar.brake();
  cout << "Current speed of the car is: " << testCar.getSpeed();
  testCar.brake();
  cout << "Current speed of the car is: " << testCar.getSpeed();
}
```