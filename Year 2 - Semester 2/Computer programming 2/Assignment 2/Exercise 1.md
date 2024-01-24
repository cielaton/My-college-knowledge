```cpp
#include <iostream>
#include <string>

using namespace std;

class Numbers {
private:
  int number;
  string lessThan20[20] = {"",        "one",       "two",      "three",
                           "four",    "five",      "six",      "seven",
                           "eight",   "nine",      "ten",      "eleven",
                           "twelve",  "thirteen",  "fourteen", "fifteen",
                           "sixteen", "seventeen", "eighteen", "nineteen"};

  string twentyTo90[10] = {"",        "",      "twenty",  "thirty", "fourty",
                           " fifty ", "sixty", "seventy", "eighty", "ninety"};

public:
  Numbers(int);
  void print() const;
};

Numbers::Numbers(int num) { number = num; }

void Numbers::print() const {
  if (number < 20)
    cout << lessThan20[number];
  else if (number >= 20 && number <= 90) {
    cout << twentyTo90[number / 10] << " " << lessThan20[number % 10];
  } else if (number >= 100 && number <= 1000) {
    cout << lessThan20[number / 100] << " hundred "
         << twentyTo90[number % 100 / 10] << " " << lessThan20[number % 10];
  } else if (number >= 1000 && number < 10000) {
    cout << lessThan20[number / 1000] << " thousand "
         << lessThan20[number % 1000 / 100] << " hundred "
         << twentyTo90[number % 1000 % 100 / 10] << " "
         << lessThan20[number % 10];
  } else
    cout << "Out of range";
}

int main() {
  unsigned int num;
  cout << "Please enter a number between 0 through 9999: ";
  cin >> num;

  Numbers testNum = Numbers(num);
  testNum.print();
}

```