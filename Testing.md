IntArray class:
```cpp
#ifndef INTARRAY_H
#define INTARRAY_H

#include <iostream>
using namespace std;

class IntArray {
private:
  int *aptr;
  int arraySize;
  void subscriptError() {
    cout << "ERROR: Subscript out of range.\n";
    exit(0);
  };

public:
  IntArray(int s) {
    arraySize = s;
    aptr = new int[s];
    for (int count = 0; count < arraySize; count++)
      *(aptr + count) = 0;
  }

  IntArray(const IntArray &obj) {
    arraySize = obj.arraySize;
    aptr = new int[arraySize];
    for (int count = 0; count < arraySize; count++)
      *(aptr + count) = *(obj.aptr + count);
  }

  int size() const { return arraySize; }
  int &operator[](const int &sub) {
    {
      if (sub < 0 || sub >= arraySize)
        subscriptError();
      return aptr[sub];
    }
  }

  ~IntArray() {
    if (arraySize > 0)
      delete[] aptr;
  };
};

#endif

```

An IntArray class dynamically creates an array of integers and performs bounds checking on the array. If an invalid subscript is used with the class, it displays an error message and aborts the program. Modify the class so it throws an exception instead



Here is the modified IntArray class that throws an exception instead of displaying an error message and aborting the program:

```cpp
#ifndef INTARRAY_H
#define INTARRAY_H

#include <iostream>
using namespace std;

class IntArray {
private:
  int *aptr;
  int arraySize;

public:
  IntArray(int s) {
    arraySize = s;
    aptr = new int[s];
    for (int count = 0; count < arraySize; count++)
      *(aptr + count) = 0;
  }

  IntArray(const IntArray &obj) {
    arraySize = obj.arraySize;
    aptr = new int[arraySize];
    for (int count = 0; count < arraySize; count++)
      *(aptr + count) = *(obj.aptr + count);
  }

  int size() const { return arraySize; }
  
  // Modified operator[] function that throws an exception
  int &operator[](const int &sub) {
    if (sub < 0 || sub >= arraySize)
      throw out_of_range("ERROR: Subscript out of range.");
    return aptr[sub];
  }

  ~IntArray() {
    if (arraySize > 0)
      delete[] aptr;
  };
};

#endif
```

In the modified class, the `subscriptError()` function is removed and the `operator[]` function is modified to throw an `out_of_range` exception if an invalid subscript is used. This exception can be caught by a try-catch block in the calling code to handle the error appropriately.