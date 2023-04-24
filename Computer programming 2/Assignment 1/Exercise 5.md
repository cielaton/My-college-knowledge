#### Class initialization:
```cpp
class Circle {
private:
  double radius;
  double pi = 3.14;

public:
  Circle();
  Circle(double);

  void setRadius(double);
  double getRadius() const;

  double getArea() const { return pi * radius * radius; }
  double getDiameter() const { return 2 * radius; }
  double getCircumference() const { return 2 * pi * radius; }
};

Circle::Circle() { radius = 0.0; }
Circle::Circle(double radius) { radius = radius; }

void Circle::setRadius(double rad) { radius = rad; }

double Circle::getRadius() const { return radius; }

```

#### Main program:
```cpp
#include <iostream>

using namespace std;

int main() {
  double rad;
  cout << "Please input the circle radius: ";
  cin >> rad;

  Circle circle(rad);
  cout << "The Area of the circle is: " << circle.getArea();
  cout << "The Diameter of the circle is: " << circle.getDiameter();
  cout << "The Circumference of the circle is: " << circle.getCircumference();
}
```