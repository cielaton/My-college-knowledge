Name: Võ Tuấn Kiệt
Class: 21ES

<center><h1>ASSIGNMENT 0</h1></center>

#### Exercise 1: 

```cpp
#include <iostream>

using namespace std;

int main() {
  int inputNum;
  while (inputNum < 1 || inputNum > 10) {
    cout << "Please input a number from 1 to 10: " << endl;
    cin >> inputNum;
  }

  cout << "The corresponding Roman number is: ";
  switch (inputNum) {
  case 1:
    cout << "I";
  case 2:
    cout << "II";
  case 3:
    cout << "III";
  case 4:
    cout << "IV";
  case 5:
    cout << "V";
  case 6:
    cout << "VI";
  case 7:
    cout << "VII";
  case 8:
    cout << "VIII";
  case 9:
    cout << "IX";
  case 10:
    cout << "X";
  default:
    break;
  }
}
```

#### Exercise 2:

```cpp
#include <iostream>

using namespace std;

int main() {
  int day, month, year;
  cout << "Please enter the following information.\n";

  cout << "Day: \n";
  cin >> day;

  cout << "Month: \n";
  cin >> month;

  cout << "Year (2 last digit): \n";
  cin >> year;

  (day * month == year) ? cout << "The date is magic"
                        : cout << "The date is not magic";
}
```

#### Exercise 3: 

```cpp 
#include <iostream>

using namespace std;

void getNumberOfDays(int arr[], int size, int mon) {
  for (int i = 0; i < size; i++) {
    if (mon == arr[i])
      cout << "The number of days is 31";
    else
      cout << "The number of days is 30";
  };
}

int main() {
  int month, year;

  while (month < 1 || month > 12) {
    cout << "Please input the following information.\n";

    cout << "Month: \n";
    cin >> month;

    cout << "Year: \n";
    cin >> year;
  }

  int months_31[] = {1, 3, 5, 7, 8, 10, 12};

  if (month == 2) {

    string isLeapYear = "The number of days is 29";
    string isNotLeapYear = "The number of days is 28";

    if (year % 100 != 0) {

      if (year % 4 == 0)
        cout << isLeapYear;
      else
        cout << isNotLeapYear;
    }

    if (year % 400) {
      cout << isLeapYear;
    } else
      cout << isNotLeapYear;
  }

  getNumberOfDays(months_31, sizeof(months_31), month);
}
```

#### Exercise 4:

```cpp
#include <iostream>

using namespace std;

int main() {
  int inputNum;
  cout << "Please input a number: \n";
  cin >> inputNum;

  int result = 0;
  for (int i = 1; i <= inputNum; i++) {
    result += i;
  }

  cout << result;
}
```

#### Exercise 5: 

```cpp
#include <iostream>

using namespace std;

int main() {
  int inputNum;
  int min, max;

  cout << "Please input your number: ";
  cin >> inputNum;

  min = inputNum;
  max = inputNum;

  while (true) {
    cout << "Please input your next number: ";
    cin >> inputNum;

    if (inputNum == -99)
      break;

    if (inputNum > max)
      max = inputNum;
    else if (inputNum < min)
      min = inputNum;
  }

  cout << "Max entered value is: " << max;
  cout << "Min entered value is: " << min;
}
```

#### Exercise 6:

```cpp
#include <iostream>

using namespace std;

double getSales(string divisionName) {
  double sales;
  cout << "Please input the " << divisionName << " quarterly sales: ";
  cin >> sales;

  return sales;
}

void findHighest(double salesArr[], string divisionsArr[]) {
  double max = salesArr[0];
  int compareIndex = 0;

  for (int i = 1; i <= 3; i++) {
    if (max < salesArr[i]) {
      max = salesArr[i];
      compareIndex = i;
    }
  }

  cout << "The highest grossing division is: " << divisionsArr[compareIndex]
       << endl
       << "Sales figure: " << max;
}

int main() {
  string divisions[] = {
      "Northeast",
      "Southeast",
      "Northwest",
      "Southwest",
  };
  double sales[] = {getSales(divisions[0]), getSales(divisions[1]),
                    getSales(divisions[2]), getSales(divisions[3])};

  findHighest(sales, divisions);
}
```

#### Exercise 7: 

```cpp
#include <iostream>

using namespace std;

void greaterVal(int arr[], int length, int n) {
  cout << "The numbers in the array that are greater than the number n:";
  for (int i = 0; i < length; i++) {
    if (arr[i] > n)
      cout << " " << arr[i];
  }
}
int main() {
  int givenArr[] = {1, 2, 3, 4, 5};
  int n = 2;

  greaterVal(givenArr, sizeof(givenArr), n);
}
```

#### Exercise 9:

```cpp
#include <iostream>

using namespace std;

int *reverse(int arr[], int length) {

  int reversedArr[length];
  int index = 0;
  for (int i = length - 1; i >= 0; i--) {
    reversedArr[index] = arr[i];
  }

  int *p = reversedArr;
  return p;
}

int main() {
  int givenArr[] = {1, 2, 3, 4, 5};

  int *p = reverse(givenArr, sizeof(givenArr));
}
```