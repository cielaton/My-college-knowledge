```cpp
#include <iostream>

using namespace std;

template <class T> T total(int num) {
  T results = 0;
  T inputVal;

  cout << "Enter the number continuously: ";
  for (int i = 0; i < num; i ++) {
    cin >> inputVal;

    results += inputVal;
  }

  return results;
}

int main() {
  int number;
  cout << "Enter the number of values you want to calculate: ";
  cin >> number;
  cout << endl;

  //Intergers
  total<int>(number);

  //Doubles
  total<double>(number);
}
```
