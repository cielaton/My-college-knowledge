#### Header file for class TestScore:
```cpp
#ifndef TESTSCORE
#define TESTSCORE

#include <iostream>
using namespace std;

template <class T> class TestScores {
private:
  int size;
  T testScores[];

public:
  TestScores(int, T[]);

  T averageTestScore();
};

template <class T> TestScores<T>::TestScores(int num, T arr[]) {
  size = num;
  for (int i = 0; i < num; i++) {
    if (testScores[i] < 0 || testScores[i] > 100)
      throw "Error: Wrong test score!\n";
    testScores[i] = arr[i];
  }
};

template <class T> T TestScores<T>::averageTestScore() {
  T total = 0;

  for (int i = 0; i < size; i++) {
    total += testScores[i];
  }

  return total / size;
};

#endif // !TESTSCORE
```

#### Main file:
```cpp
#include <iostream>

#include "header1.h"

using namespace std;

int main() {
  int testArr[5] = {1, 2, 3, 4, 5};

  try {
    TestScores<int> testScore = TestScores<int>(5,testArr);
    cout << "The average test score is: " << testScore.averageTestScore();
  }

  catch (char const *exeception) {
    cout << exeception;
  }
}
```