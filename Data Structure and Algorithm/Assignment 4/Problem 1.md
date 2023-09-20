Contents of **NumberLinkedList.h**
```cpp
#ifndef NUMBERLINKEDLIST
#define NUMBERLINKEDLIST

#include <cstddef>
class NumberLinkedList {
private:
    struct ListNode {
        int value;
        struct ListNode *next;
    };
    ListNode *head;

public:
    NumberLinkedList() {
        head = nullptr;
    }
    ~NumberLinkedList();

    bool isEmpty() {
        return head == nullptr;
    }

    void insertFirst(int);
    void insertLast(int);
    void deleteFirst();
    void deleteLast();
    int length();
    void deleteNode(int);
    void displayList() const;
};

#endif // !NUMBERLINKEDLIST
```

Contents of **NumberLinkedList.cpp**
```cpp
#include "./NumberLinkedList.h"
#include <iostream>
using namespace std;

struct ListNode {
    int value;
    struct ListNode *next;
};

NumberLinkedList::~NumberLinkedList() {
    ListNode *p = head;
    ListNode *temporaryNode = new ListNode;
    while (p) {
        temporaryNode = p;
        p = p->next;
        delete temporaryNode;
    }
}

void NumberLinkedList::insertFirst(int value) {
    ListNode *newNode = new ListNode;
    newNode->value = value;
    newNode->next = head;
    head = newNode;
}

void NumberLinkedList::insertLast(int value) {
    ListNode *newNode = new ListNode;
    newNode->value = value;
    newNode->next = nullptr;

    ListNode *p = head;
    if (p == nullptr) {
        head = newNode;
        return;
    }

    while (p) {
        if (p->next == nullptr) {
            p->next = newNode;
            return;
        }
        p = p->next;
    }
}


void NumberLinkedList::deleteFirst() {
    if (isEmpty()) {
        cout << "The list is empty! Nothing to remove" << endl;
        return;
    }
    ListNode *temporaryNode = head;
    head = head->next;
    delete temporaryNode;
}

void NumberLinkedList::deleteLast() {
    if (isEmpty()) {
        cout << "The list is empty! Nothing to remove" << endl;
        return;
    }
    ListNode *p = head;
    while (p) {
        if (p->next->next == nullptr) {
            delete p->next;
            p->next = nullptr;
        }
        p = p->next;
    }
}

int NumberLinkedList::length() {
    int count = 0;
    ListNode *p = head;
    while (p) {
        count++;
        p = p->next;
    }
    return count;
}

void NumberLinkedList::deleteNode(int value) {
    ListNode *p = head;
    while (p) {
        if (p->next->value == value) {
            delete p->next;
            p->next = p->next->next;
        }
        p = p->next;
    }
}
void NumberLinkedList::displayList() const {
    int count = 1;
    ListNode *p = head;
    if (p == nullptr) {
        cout << "The list is empty!" << endl;
        return;
    }
    while (p) {
        cout << "Node " << count << ": " << p->value << endl;
        p = p->next;
        count++;
    }
}
```

Test file:
```cpp
#include <iostream>
#include "./NumberLinkedList.h"
#include "./NumberLinkedList.cpp"

using namespace std;

int main() {
    NumberLinkedList testList;
    cout << "Empty check: " << testList.isEmpty() << endl;
    cout << "List lenght: " << testList.length() << endl << endl;

    cout << "Add node:" << endl;
    testList.insertFirst(10);
    testList.insertFirst(20);
    testList.insertFirst(30);
    testList.displayList();

    cout << "Delete First:" << endl;
    testList.deleteFirst();
    testList.displayList();

    cout << "Delete Last:" << endl;
    testList.deleteLast();
    testList.displayList();

    cout << "Final lenght: " << testList.length() << endl;
}
```