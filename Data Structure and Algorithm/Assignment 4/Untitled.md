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

Write the following functions manipulating on linked lists which are defined in NumberLinkedList.cpp: a) insertFirst(int item): inserting an item into the linked list at the beginning of the list. b) insertLast(int item): inserting an item into the linked list at the end of the list. c) deleteFirst(): deleting the item at the beginning of the list. d) deleteLast(): deleting the item at the end of the list. e) length(): computing the number of elements of the list. f) delete(int i): deleting an i-th node from a linked list. g) displayList(): displaying all the values stored in the linked list.

