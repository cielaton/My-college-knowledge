```cpp
#include <iostream>
#include <vector>

using namespace std;

void takingInput(vector<double> &vec) {
  cout << "Enter the rainfall for each 12 months: ";

  for (int i = 0; i < 12; i++) {
    double inputValue;
    cin >> inputValue;

    if (inputValue < 0)
      throw "Error: Rainfall value must be positive!";

    vec.push_back(inputValue);
  }

  cout << endl;
}

double totalRainfall(vector<double> vec) {
  double total = 0;

  for (int i = 0; i < vec.size(); i++) {
    total += vec[i];
  }

  return total;
}

double averageMonthlyRainfall(vector<double> vec) {
  double total = totalRainfall(vec);
  return total / 12;
}

void comparison(vector<double> vec) {
  int maxElementsMonth = 0;
  int minElementsMonth = 0;

  for (int i = 0; i < vec.size(); i++) {
    if (vec[i] > vec[maxElementsMonth])
      maxElementsMonth = i;

    else if (vec[i] < vec[minElementsMonth])
      minElementsMonth = i;
  }

  cout << "The month with the highest amount is: " << maxElementsMonth + 1 << endl;
  cout << "The month with the lowest amount is: " << minElementsMonth + 1 << endl;
}

int main() {
  vector<double> rainfall;

  try {
    takingInput(rainfall);
  } catch (char *exception) {
    cout << exception;
  }
  
  cout << "The total rainfall for the year is: " << totalRainfall(rainfall) << endl;
  cout << "The average monthly rainfall is: "
       << averageMonthlyRainfall(rainfall) << endl;
  comparison(rainfall);
}
```
