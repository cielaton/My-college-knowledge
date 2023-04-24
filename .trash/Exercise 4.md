#### Header file for class SimpleVector:
```cpp
// SimpleVector class template
#ifndef SIMPLEVECTOR_H
#define SIMPLEVECTOR_H

#include <cstdlib>
#include <iostream>
#include <new>

using namespace std;

template <class T> class SimpleVector {
private:
  T *aptr; // To point to the allocated array
  int arraySize;
  void memError(); // Handles memory allocation errors
  void subError(); // Handles subscripts out of range

public:
  // modified function
  void push_back(T);
  void pop_back(T);

  SimpleVector() {
    aptr = 0;
    arraySize = 0;
  }
  SimpleVector(int);
  SimpleVector(const SimpleVector &);
  ~SimpleVector();

  // Accessor to return the array size
  int size() const { return arraySize; }
  // Accessor to return a specific element
  T getElementAt(int position);
  // Overloaded [] operator declaration
  T &operator[](const int &);
};

template <class T> void SimpleVector<T>::push_back(T value) {
  T *tempArray = aptr;
  arraySize += 1;

  aptr = new T[arraySize];
  for (int i = 0; i < arraySize - 1; i++) {
    *(aptr + i) = *(tempArray + i);
  }

  *(aptr + arraySize - 1) = value;
  delete tempArray;
}

template <class T> void SimpleVector<T>::pop_back(T value) {
  T *tempArray = aptr;
  arraySize -= 1;

  aptr = new T[arraySize];
  for (int i = 0; i < arraySize; i++) {
    *(aptr + i) = *(tempArray + 1);
  }

  delete tempArray;
}

template <class T> SimpleVector<T>::SimpleVector(int s) {
  arraySize = s;
  // Allocate memory for the array.
  try {
    aptr = new T[s];
  } catch (bad_alloc) {
    memError();
  }
  // Initialize the array.
  for (int count = 0; count < arraySize; count++)
    *(aptr + count) = 0;
}
//*******************************************
// Copy Constructor for SimpleVector class. *
//*******************************************
template <class T> SimpleVector<T>::SimpleVector(const SimpleVector &obj) {
  // Copy the array size.
  arraySize = obj.arraySize;
  // Allocate memory for the array.
  aptr = new T[arraySize];
  if (aptr == 0)
    memError();
  // Copy the elements of obj's array.
  for (int count = 0; count < arraySize; count++)
    *(aptr + count) = *(obj.aptr + count);
}
//**************************************
// Destructor for SimpleVector class. *
//**************************************
template <class T> SimpleVector<T>::~SimpleVector() {
  if (arraySize > 0)
    delete[] aptr;
}
//********************************************************
// memError function. Displays an error message and *
// terminates the program when memory allocation fails. *
//********************************************************
template <class T> void SimpleVector<T>::memError() {
  cout << "ERROR:Cannot allocate memory.\n";
  exit(EXIT_FAILURE);
}
//************************************************************
// subError function. Displays an error message and *
// terminates the program when a subscript is out of range. *
//************************************************************
template <class T> void SimpleVector<T>::subError() {
  cout << "ERROR: Subscript out of range.\n";
  exit(EXIT_FAILURE);
}
//*******************************************************
// getElementAt function. The argument is a subscript. *
// This function returns the value stored at the *
// subcript in the array. *
//*******************************************************
template <class T> T SimpleVector<T>::getElementAt(int sub) {
  if (sub < 0 || sub >= arraySize)
    subError();
  return aptr[sub];
}
//********************************************************
// Overloaded [] operator. The argument is a subscript. *
// This function returns a reference to the element *
// in the array indexed by the subscript. *
//********************************************************
template <class T> T &SimpleVector<T>::operator[](const int &sub) {
  if (sub < 0 || sub >= arraySize)
    subError();
  return aptr[sub];
}
#endif
```

#### Main file:
```cpp
#include <iostream>

#include "header1.h"

using namespace std;

int main() {
  int size;

  cout << "Enter the array size: ";
  cin >> size;
  cout << endl;

  int valueToBePush = 10;

  SimpleVector<int> sampleVec = SimpleVector<int>(size);
  sampleVec.push_back(valueToBePush);
  cout << "The vector size after being pushed: " << sampleVec.size();
  cout << "The element pushed into the array at the last index: "
       << sampleVec.getElementAt(size);
}
```