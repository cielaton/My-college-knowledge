### Header for class BasicShape:

```cpp
#include <iostream>

#ifndef BASICSHAPE
#define BASICSHAPE

class BasicShape {
private:
  double area;

public:
  double getArea() const { return area; }
  virtual double calcArea() = 0;
};

#endif // !BASICSHAPE
```

### Header for class Circle:

```cpp
#include "header1.h"
#include <iostream>

#ifndef CIRCLE
#define CIRCLE

class Circle : public BasicShape {
private:
  long int centerX, centerY;
  long double radius;

public:
  Circle(long int x, long int y, long double r) {
    centerX = x;
    centerY = y;
    radius = r;
    calcArea();
  }

  long double getCenterX() const {return centerX;}
  long double getCenterY() const {return centerY;}

  double calcArea() {
    return 3.14159 * radius * radius;
  }
  
};

#endif // !CIRCLE
```

### Header for class Rectangle:

```cpp
#include <iostream>
#include "header1.h"

#ifndef RECTANGLE
#define RECTANGLE

class Rectangle: public BasicShape {
private: 
  long int width, length;

public:
  Rectangle(long int w, long int l) {
    width = w;
    length = l;
    calcArea();
  }

  long int getWidth() const {return width;}
  long int getLength() const {return length;}

  double calcArea() {return width * length;}

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

int main () {
  Circle circle(0,0,20);
  Rectangle rect(10, 20);

  cout << "The area of the circle is: " << circle.calcArea() << endl;
  cout << "The area of the rectangle: " << rect.calcArea(); 
}
```