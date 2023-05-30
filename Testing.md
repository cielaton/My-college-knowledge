Write a bool function that uses recursion to determine if a string argument is a palindrome. The function should return true if the argument reads the same forward and backward.
Write the solution in Cpp using recursive and make sure there is no error.



```cpp
#include <iostream>
#include <string>

using namespace std;

bool isPalindrome(string str, int start, int end) {
    if (start >= end) {
        return true;
    }
    if (str[start] != str[end]) {
        return false;
    }
    return isPalindrome(str, start + 1, end - 1);
}

int main() {
    string str = "racecar";
    bool palindrome = isPalindrome(str, 0, str.length() - 1);
    if (palindrome) {
        cout << str << " is a palindrome." << endl;
    } else {
        cout << str << " is not a palindrome." << endl;
    }
    return 0;
}
``` 

Output:
```
racecar is a palindrome.
```