A file filter reads an input file, transforms it in some way, and writes the results to an output file. Write an
abstract file filter class that defines a pure virtual function for transforming a character. Create one derived
class of your file filter class that performs encryption, another that transforms a file to all uppercase, and
another that creates an unchanged copy of the original file. The class should have the following member
function:
void doFilter(ifstream &in, ofstream &out)
This function should be called to perform the actual filtering. The member function for transforming a
single character should have the prototype:
char transform(char ch)
The encryption class should have a constructor that takes an integer as an argument and uses it as the
encryption key.

Write a solution for the above program in C++, make sure it run flawlessly without error.



Here is a possible solution:

```c++
#include <iostream>
#include <fstream>
#include <string>

using namespace std;

class FileFilter {
public:
    virtual char transform(char ch) = 0;
    void doFilter(ifstream& in, ofstream& out) {
        char ch;
        while (in.get(ch)) {
            out.put(transform(ch));
        }
    }
};

class EncryptionFilter : public FileFilter {
private:
    int key;
public:
    EncryptionFilter(int key) : key(key) {}
    char transform(char ch) {
        return ch ^ key; // simple XOR encryption
    }
};

class UppercaseFilter : public FileFilter {
public:
    char transform(char ch) {
        return toupper(ch);
    }
};

class CopyFilter : public FileFilter {
public:
    char transform(char ch) {
        return ch;
    }
};

int main() {
    ifstream in("input.txt");
    ofstream out_enc("output_encrypted.txt");
    ofstream out_upper("output_uppercase.txt");
    ofstream out_copy("output_copy.txt");

    if (!in || !out_enc || !out_upper || !out_copy) {
        cerr << "Error: could not open files." << endl;
        return 1;
    }

    EncryptionFilter enc_filter(42); // encryption key = 42
    UppercaseFilter upper_filter;
    CopyFilter copy_filter;

    enc_filter.doFilter(in, out_enc);
    
	in.clear(); // reset file flag to read from the beginning
	in.seekg(0, ios::beg); // move file pointer to the beginning
	
	upper_filter.doFilter(in, out_upper);

	in.clear();
	in.seekg(0, ios::beg);
	
	copy_filter.doFilter(in, out_copy);

	cout << "Files processed successfully." << endl;

	return 0;
}
```

In this solution, we define the abstract base class `FileFilter` with a pure virtual function `transform` and a non-virtual function `doFilter` that reads from an input file and writes to an output file using the `transform` function. We also define three derived classes: `EncryptionFilter`, which performs a simple XOR encryption using a user-defined key; `UppercaseFilter`, which transforms all characters to uppercase; and `CopyFilter`, which creates an exact copy of the input file.

In the `main` function, we open four files: the input file and