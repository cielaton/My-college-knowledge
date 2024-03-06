#### Header file:
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
    int cannotAccess;

public:
    NumberLinkedList() {
        head = nullptr;
    }
    // Copy constructor
    NumberLinkedList(NumberLinkedList &toBeCopied) {
        head = nullptr;
        *this = toBeCopied;
    }
    ~NumberLinkedList();

    bool isEmpty() {
        return head == nullptr;
    }

    ListNode *getHead() const {
        return head;
    }
    void setHeadNull() {
        head = nullptr;
    }

    // Assignment operator overloading
    NumberLinkedList &operator=(NumberLinkedList &);

    void insertFirst(int);
    void insertLast(int);
    void deleteFirst();
    void deleteLast();
    int length();
    void deleteNode(int);
    void displayList() const;

    void merge(NumberLinkedList &);
    void concatenate(NumberLinkedList &);
    bool equal(NumberLinkedList);

    void insertSorted(int);

    bool isSet();
    bool isSubsetOf(NumberLinkedList &);
    NumberLinkedList unionWith(NumberLinkedList &);
    NumberLinkedList intersectionWith(NumberLinkedList &);
};

#endif // !NUMBERLINKEDLIST
```

#### Function definition file:
```cpp
#include "./NumberLinkedList.h"
#include <iostream>
#include <memory>
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

NumberLinkedList &NumberLinkedList::operator=(NumberLinkedList &toBeAssigned) {

    ListNode *p = toBeAssigned.getHead();
    while (p) {
        insertLast(p->value);
        p = p->next;
    }

    return *this;
}

void NumberLinkedList::merge(NumberLinkedList &toBeMerged) {
    ListNode *pThis = head;
    ListNode *pToBeMerged = toBeMerged.getHead();
    ListNode *pToBeMergedNextNode = toBeMerged.getHead();

    if (pThis == nullptr) {
        pThis = pToBeMerged;
        return;
    } else if (pToBeMerged == nullptr)
        return;

    // checking both condition to prevent pThis->next == nullprt which cause error
    // when access pThis->next->value
    while (pThis && pThis->next) {
        if (pThis->value <= pToBeMerged->value &&
                pThis->next->value >= pToBeMerged->value) {
            // Copy the next node of the first node of toBeMerged
            pToBeMergedNextNode = pToBeMerged->next;

            pToBeMerged->next = pThis->next;
            pThis->next = pToBeMerged;
            // First node now point to the next Node in toBeMerged list
            pToBeMerged = pToBeMergedNextNode;
        }

        if (pThis->next->next == nullptr) {
            pThis->next->next = pToBeMergedNextNode;
            toBeMerged.setHeadNull();
            return;
        }

        pThis = pThis->next;
    }
}

void NumberLinkedList::concatenate(NumberLinkedList &toBeConcat) {
    ListNode *pThis = head;

    if (pThis == nullptr) {
        pThis = toBeConcat.getHead();
        return;
    } else if (toBeConcat.getHead() == nullptr) {
        return;
    }

    while (pThis) {
        if (pThis->next == nullptr) {
            {
                pThis->next = toBeConcat.getHead();
                toBeConcat.setHeadNull();
                return;
            }
        }
        pThis = pThis->next;
    }
}

bool NumberLinkedList::equal(NumberLinkedList toBeCompared) {
    ListNode *pThis = head;
    ListNode *pToBeCompared = toBeCompared.getHead();
    bool isEqual = false;

    while (pThis) {
        if (pThis->value == pToBeCompared->value &&
                length() == toBeCompared.length())
            isEqual = true;
        else
            isEqual = false;

        pThis = pThis->next;
        pToBeCompared = pToBeCompared->next;
    }
    return isEqual;
}

void NumberLinkedList::insertSorted(int value) {
    ListNode *p = head;
    ListNode *toBeAdded = new ListNode;
    toBeAdded->value = value;

    // The list is already sorted => The list is not empty => No need to check for
    // null head case
    while (p) {
        if (value >= p->value) {
            toBeAdded->next = p->next;
            p->next = toBeAdded;
            break;

        } else {
            toBeAdded->next = head;
            head = toBeAdded;
            break;
        }
        p = p->next;
    }
}

bool NumberLinkedList::isSet() {
    // Since the set is created by Linked list => always true
    return true;
}

bool NumberLinkedList::isSubsetOf(NumberLinkedList &toBeChecked) {
    ListNode *pThis = head;
    ListNode *pTobeChecked;
    bool isSubset = false;

    if (pThis == nullptr)
        return true;
    else if (toBeChecked.getHead() == nullptr)
        return false;

    while (pThis) {
        bool isMatch = false;
        pTobeChecked = toBeChecked.getHead();
        while (pTobeChecked) {
            if (pThis->value == pTobeChecked->value) {
                isMatch = true;
                break;
            }
            pTobeChecked = pTobeChecked->next;
        }
        if (!isMatch) {
            isSubset = false;
            break;
        }
        isSubset = true;
        pThis = pThis->next;
    }

    return isSubset;
}

NumberLinkedList
NumberLinkedList::intersectionWith(NumberLinkedList &secondList) {
    NumberLinkedList temporaryList;
    ListNode *pThis = head;
    ListNode *pSecondList;

    if (pThis == nullptr || secondList.getHead() == nullptr)
        return temporaryList;
    while (pThis) {
        pSecondList = secondList.getHead();
        while (pSecondList) {
            if (pThis->value == pSecondList->value)
                temporaryList.insertLast(pThis->value);
            pSecondList = pSecondList->next;
        }
        pThis = pThis->next;
    }
    return temporaryList;
}

NumberLinkedList NumberLinkedList::unionWith(NumberLinkedList &secondList) {
    NumberLinkedList temporaryList = secondList;
    ListNode *pThis = head;
    ListNode *pSecondList;
    bool isFullyNotEqualNode = false;

    if (pThis == nullptr)
        return secondList;
    else if (secondList.getHead() == nullptr)
        return *this;

    while (pThis) {
        pSecondList = secondList.getHead();
        while (pSecondList) {
            if (pThis->value == pSecondList->value) {
                isFullyNotEqualNode = false;
                break;
            }
            isFullyNotEqualNode = true;
            pSecondList = pSecondList->next;
        }
        if (isFullyNotEqualNode == true)
            temporaryList.insertLast(pThis->value);
        pThis = pThis->next;
    }
    return temporaryList;
}
```

#### Main file:
```cpp
#include "./NumberLinkedList.cpp"
#include "./NumberLinkedList.h"
#include <iostream>

using namespace std;

int main() {
    NumberLinkedList testList1;
    NumberLinkedList testList2;

    for (int i = 2; i <= 4; i += 2) {
        testList1.insertLast(i);
    }

    for (int i = 2; i <= 10; i += 2) {
        testList2.insertLast(i);
    }

    cout << "Content of list 1:" << endl;
    testList1.displayList();
    cout << endl;

    cout << "Content of list 2: " << endl;
    testList2.displayList();
    cout << endl;

    cout << "Is subset: " << testList1.isSubsetOf(testList2) << endl;

    // NumberLinkedList intersectionedList =
    // testList1.intersectionWith(testList2); cout << "Intersectioned list: " <<
    // endl; intersectionedList.displayList();

    NumberLinkedList unionedList = testList1.unionWith(testList2);
    cout << "Unioned List: " << endl;
    unionedList.displayList();
}

```