#### Question 1:
```cpp
#include <iostream>

using namespace std;

int main() {
    string name, studentClass;
    /* Đặt là studentClass bởi vì "class" trùng với keyword trong C++ nên không được
     * phép đặt (code giấy thì thầy chả quan tâm đâu) */
    int age;
    float GPA;

    cout << "Enter the student name: ";
    cin >> name;

    cout << "Enter the student class: ";
    cin >> studentClass;

    cout << "Enter the student age: ";
    cin >> age;
    while (age < 0) {
        cout << "Invalid age, please enter again: ";
        cin >> age;
    }

    cout << "Enter GPA score: ";
    cin >> GPA;
    while (GPA < 0 || GPA > 4) {
        cout << "Invalid GPA, please enter again: ";
        cin >> GPA;
    }

    cout << endl;
    cout << "Name: " << name << endl;
    cout << "Class: " << studentClass << endl;
    cout << "Age: " << age << endl;
    cout << "GPA: " << GPA << endl;
}
```

#### Question 2:
```cpp
#include <iostream>

using namespace std;

int main() {
    int n;
    cout << "Enter the number of integers: ";
    cin >> n;
    while (n < 1) {
        cout << "Invalid value, please enter again: ";
        cin >> n;
    }

    int enteredNum, sumOfOdd = 0;
    for (int i = 0; i < n; i++) {
        cout << "Enter the numer: ";
        cin >> enteredNum;

        if (enteredNum % 2 != 0)
            sumOfOdd += enteredNum;
    }

    cout << "Sum of odd numbers: " << sumOfOdd;
}
```

#### Question 3: 
```cpp
#include <iostream>

using namespace std;

float minimum(float num1, float num2) {
    if (num1 < num2)
        return num1;
    else
        return num2;
}

int main() {
    float testNum1, testNum2, testNum3, testNum4;

    cout << "Enter 4 real numbers: ";
    cin >> testNum1 >> testNum2 >> testNum3 >> testNum4;

    float firstMinimum = minimum(testNum1, testNum2);
    float secondMinimum = minimum(testNum3, testNum4);

    cout << "The minimum number of four real numbers: "
         << minimum(firstMinimum, secondMinimum);
}
```

#### Question 4:
```cpp
#include <iostream>

using namespace std;

void minimumAndMaximum(float num1, float num2, float num3, float &min,
                       float &max) {
    min = num1;
    max = num1;

    if (min > num2)
        min = num2;
    if (min > num3)
        min = num3;

    if (max < num2)
        max = num2;
    if (max < num3)
        max = num3;
}

int main() {
    float testNum1, testNum2, testNum3, min, max;

    cout << "Enter three numbers: ";
    cin >> testNum1 >> testNum2 >> testNum3;

    minimumAndMaximum(testNum1, testNum2, testNum3, min, max);
    cout << "Minimum: " << min << endl;
    cout << "Maximum: " << max << endl;
}
```