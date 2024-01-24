### Header file for PersonData class
```cpp
#include <iostream>
#include <string>

using namespace std;

#ifndef PERSONDATA_H
#define PERSONDATA_H

class PersonData {
private:
  string firstName, lastName;
  string address, city, state;
  int zip;
  int phone;

public:
  PersonData()
      : firstName(""), lastName(""), address(""), city(""), state(""), zip(0),
        phone(0){};
  PersonData(string, string, string, string, string, int, int);

  void setFirstName(string);
  void setLastName(string);
  void setAddress(string);
  void setCity(string);
  void setState(string);
  void setZip(int);
  void setPhone(int);

  string getFirstName() const;
  string getLastName() const;
  string getAddress() const;
  string getCity() const;
  string getState() const;
  int getZip() const;
  int getPhone() const;
};

PersonData::PersonData(string fName, string lName, string addr,
                       string givenCity, string givenState, int zipCode,
                       int phoneNum) {
  firstName = fName;
  lastName = lName;
  address = addr;
  city = givenCity;
  state = givenState;
  zip = zipCode;
  phone = phoneNum;
}

void PersonData::setFirstName(string fName) { firstName = fName; }
void PersonData::setLastName(string lName) { lastName = lName; }
void PersonData::setAddress(string add) { address = add; }
void PersonData::setCity(string givenCity) { city = givenCity; }
void PersonData::setState(string givenState) { state = givenState; }
void PersonData::setZip(int zipCode) { zip = zipCode; }
void PersonData::setPhone(int num) { phone = num; }

string PersonData::getFirstName() const { return firstName; }
string PersonData::getLastName() const { return lastName; }
string PersonData::getAddress() const { return address; }
string PersonData::getCity() const { return city; }
string PersonData::getState() const { return state; }
int PersonData::getZip() const { return zip; }
int PersonData::getPhone() const { return phone; }

#endif
```

### Header file for CustomerData class
```cpp
#include "header1.h"

#ifndef CUSTOMERDATA_H
#define CUSTOMERDATA_H

class CustomerData : public PersonData {
private:
  int customerNumber;
  bool mailingList;

public:
  CustomerData() : customerNumber(0), mailingList(0){};
  CustomerData(string, string, string, string, string, int, int, int, bool);

  void setCustomerNumber(int);
  void setMailingList(bool);

  int getCustomerNumber() const;
  bool getMailingList() const;
};

CustomerData::CustomerData(string fName, string lName, string addr,
                           string givenCity, string givenState, int zipCode,
                           int phoneNum, int customerNum, bool mailList)
    : PersonData(fName, lName, addr, givenCity, givenState, zipCode, phoneNum) {
  customerNumber = customerNum;
  mailingList = mailList;
}

void CustomerData::setCustomerNumber(int num) { customerNumber = num; }
void CustomerData::setMailingList(bool cond) { mailingList = cond; }

int CustomerData::getCustomerNumber() const { return customerNumber; }
bool CustomerData::getMailingList() const { return mailingList; }

#endif
```

### Main file
```cpp
#include <iostream>

#include "header1.h"
#include "header2.h"

using namespace std;

int main() {
  string fName, lName, addr, givenCity, givenState;
  int zipCode, phoneNum, customerNum;
  bool mailList;

  cout << "Please input the following customer data: " << endl;
  cout << " First name: ";
  cin >> fName;
  cout << endl;

  cout << "Last name: ";
  cin >> lName;
  cout << endl;

  cout << "Address: ";
  cin >> addr;
  cout << endl;

  cout << "City: ";
  cin >> givenCity;
  cout << endl;

  cout << "State: ";
  cin >> givenState;
  cout << endl;

  cout << "Zip code: ";
  cin >> zipCode;
  cout << endl;

  cout << "Phone number: ";
  cin >> phoneNum;
  cout << endl;

  cout << "Customer number: ";
  cin >> customerNum;
  cout << endl;

  cout << "Mailing list(true/false)?: ";
  cin >> mailList;
  cout << endl;

  CustomerData customer1(fName, lName, addr, givenCity, givenState, zipCode,
                         phoneNum, customerNum, mailList);

  cout << customer1.getPhone();
}
```