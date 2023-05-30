Write a recursive function that accepts a string object as its argument and prints the string in reverse order.

Write the solution in Cpp using recursive and make sure there is no error.



Here's a possible solution in C++:

```cpp
#include <iostream>
#include <string>

void printReverse(const std::string& str, int i) {
    if (i >= 0) {
        std::cout << str[i];
        printReverse(str, i-1);
    }
}

int main() {
    std::string input;
    std::cout << "Enter a string: ";
    getline(std::cin, input);
    printReverse(input, input.length()-1);
    return 0;
}
```

The `printReverse` function takes two arguments: the string to be printed in reverse order and the index of the current character being printed. If the index is greater than or equal to zero (i.e., there are still characters left to print), it prints the character at that index and then calls itself with the previous index (i-1). This recursion continues until all characters have been printed.

In `main`, we simply get a string input from the user and call `printReverse` with the length of the string minus one (since indices start at zero). The output should be the input string in reverse order.