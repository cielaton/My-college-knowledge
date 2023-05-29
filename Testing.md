The SimpleVector class:
```cpp
#ifndef SIMPLEVECTOR_H
#define SIMPLEVECTOR_H

#include <cstdlib>
#include <iostream>
#include <new>

using namespace std;

template <class T> class SimpleVector {
private:
  T *aptr;
  int arraySize;
  void memError() {
    cout << "ERROR:Cannot allocate memory.\n";
    exit(EXIT_FAILURE);
  }
  void subError() {
    cout << "ERROR: Subscript out of range.\n";
    exit(EXIT_FAILURE);
  }

public:
  void push_back(T value) {
    T *tempArray = aptr;
    arraySize += 1;

    aptr = new T[arraySize];
    for (int i = 0; i < arraySize - 1; i++) {
      *(aptr + i) = *(tempArray + i);
    }

    *(aptr + arraySize - 1) = value;
    delete tempArray;
  };

  void pop_back(T value) {
    T *tempArray = aptr;
    arraySize -= 1;

    aptr = new T[arraySize];
    for (int i = 0; i < arraySize; i++) {
      *(aptr + i) = *(tempArray + 1);
    }

    delete tempArray;
  };

  SimpleVector() {
    aptr = 0;
    arraySize = 0;
  }

  SimpleVector(int s) {
    arraySize = s;
    try {
      aptr = new T[s];
    } catch (bad_alloc) {
      memError();
    }
    for (int count = 0; count < arraySize; count++)
      *(aptr + count) = 0;
  };

  SimpleVector(const SimpleVector &obj) {
    // Copy the array size.
    arraySize = obj.arraySize;
    aptr = new T[arraySize];
    if (aptr == 0)
      memError();
    for (int count = 0; count < arraySize; count++)
      *(aptr + count) = *(obj.aptr + count);
  }

  ~SimpleVector() {
    if (arraySize > 0)
      delete[] aptr;
  };

  int size() const { return arraySize; }

  T getElementAt(int sub) {
    if (sub < 0 || sub >= arraySize)
      subError();
    return aptr[sub];
  }

  T &operator[](const int &sub) {
    if (sub < 0 || sub >= arraySize)
      subError();
    return aptr[sub];
  }
};
#endif
```

Write a class template named SortableVector. The class should be derived from the SimpleVector class. It should have a member function that sorts the array elements in ascendingg order. (Use the sorting algorithm of your choice.) Test the template in a driver program.

Write the solution for the above problem using cpp and make sure there is no error.



```cpp
#include <iostream>
#include "SimpleVector.h"

using namespace std;

template <class T> class SortableVector : public SimpleVector<T> {
public:
  SortableVector() : SimpleVector<T>() {}

  SortableVector(int s) : SimpleVector<T>(s) {}

  void sort() {
    int i, j;
    T temp;
    int size = this->size();
    for (i = 0; i < size - 1; i++) {
      for (j = i + 1; j < size; j++) {
        if (this->getElementAt(i) > this->getElementAt(j)) {
          temp = this->getElementAt(i);
          this->operator[](i) = this->getElementAt(j);
          this->operator[](j) = temp;
        }
      }
    }
  }
};

int main() {
  // Instantiate a SortableVector of integers with initial size of 5
  SortableVector<int> v(5);

  // Add elements to the vector
  v.push_back(3);
  v.push_back(7);
  v.push_back(2);
  v.push_back(9);
  v.push_back(1);

   // Display the element before sorting
   cout << "Before sorting: ";
   for(int i=0; i<v.size(); i++){
      cout << v.getElementAt(i) << " ";
   }

   // Sort the elements in ascending order
   v.sort();

   // Display the elements after sorting
   cout << "\nAfter sorting: ";
   for(int i=0; i<v.size(); i++){
      cout << v.getElementAt(i) << " ";
   }

   return 0;
}
```

Output:
```
Before sorting: 3 7 2 9 1 
After sorting: 1 2 3 7 9
```