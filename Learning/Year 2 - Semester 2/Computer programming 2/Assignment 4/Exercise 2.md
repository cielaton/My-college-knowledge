```cpp
#include <iostream>

using namespace std;

template <class T> T minimum(T val1, T val2) {
  return (val1 < val2) ? val1 : val2;
}
template <class T> T maximum(T val1, T val2) {
  return (val1 > val2) ? val1 : val2;
}

int main() {
  //For intergers
  int intValue1, intValue2;

  cout << "Enter the 2 values you want to compare: " << endl;
  cin >> intValue1 >> intValue2;
  cout << endl;

  minimum(intValue1, intValue2);
  maximum(intValue1, intValue2);

  //For doubles
  double doubleValues1, doubleValues2;

  cout << "Enter the 2 values you want to compare: " << endl;
  cin >> doubleValues1 >> doubleValues2;
  cout << endl;

  minimum(doubleValues1, doubleValues2);
  maximum(doubleValues1, doubleValues2);
}
```
