### Header file for PersonData:

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

  PersonData(string fName, string lName, string addr, string givenCity,
             string givenState, int zipCode, int phoneNum) {
    firstName = fName;
    lastName = lName;
    address = addr;
    city = givenCity;
    state = givenState;
    zip = zipCode;
    phone = phoneNum;
  }

  void setFirstName(string fName) { firstName = fName; }
  void setLastName(string lName) { lastName = lName; }
  void setAddress(string add) { address = add; }
  void setCity(string givenCity) { city = givenCity; }
  void setState(string givenState) { state = givenState; }
  void setZip(int zipCode) { zip = zipCode; }
  void setPhone(int num) { phone = num; }

  string getFirstName() const { return firstName; }
  string getLastName() const { return lastName; }
  string getAddress() const { return address; }
  string getCity() const { return city; }
  string getState() const { return state; }
  int getZip() const { return zip; }
  int getPhone() const { return phone; }
};

#endif
```

### Header file for CustomerData:

```cpp
#include "header1.h"

#ifndef CUSTOMERDATA_H
#define CUSTOMERDATA_H

class CustomerData : public PersonData {
private:
  int customerNumber;
  bool mailingList;
  PersonData personData;

public:
  CustomerData() : customerNumber(0), mailingList(0){};
  CustomerData(PersonData data, int customerNum, bool mailList)
      : PersonData(data.getFirstName(), data.getLastName(), data.getAddress(),
                   data.getCity(), data.getState(), data.getZip(),
                   data.getPhone()) {
    personData = data;
    customerNumber = customerNum;
    mailingList = mailList;
  }

  void setCustomerNumber(int num) { customerNumber = num; }
  void setMailingList(bool cond) { mailingList = cond; }
  void setPersonData(PersonData data) { personData = data; }

  int getCustomerNumber() const { return customerNumber; }
  bool getMailingList() const { return mailingList; }
  PersonData getPersonData() const { return personData; }
};

#endif
```

### Header file for PreferedCustomer:

```cpp
#include "header2.h"
#include <string>

#ifndef PREFERREDCUSTOMER_H
#define PREFERREDCUSTOMER_H

class PreferredCustomer : public CustomerData {
private:
  double purchasesAmount, discountLevel;
  double discountLevelValue[4] = {5, 6, 7, 10};

public:
  PreferredCustomer(CustomerData data, double amount)
      : CustomerData(data.getPersonData(), data.getCustomerNumber(),
                     data.getMailingList()) {
    purchasesAmount = amount;
    if (purchasesAmount == 500)
      discountLevel = discountLevelValue[0];
    else if (purchasesAmount == 1000)
      discountLevel = discountLevelValue[1];
    else if (purchasesAmount == 1500)
      discountLevel = discountLevelValue[2];
    else if (purchasesAmount == 2000)
      discountLevel = discountLevelValue[3];
  }

  void setPurchasesAmount(double amount) { purchasesAmount = amount; }
  void setDiscountLevel(double level) { discountLevel = level; }

  double getPurchasesAmount() const { return purchasesAmount; }
  double getDiscountLevel() const { return discountLevel; }
};

#endif
```

### Main file:

```cpp
#include <iostream>

#include "header1.h"
#include "header2.h"
#include "header3.h"

using namespace std;

int main() {
  string fName, lName, addr, givenCity, givenState;
  int zipCode, phoneNum, customerNum;
  bool mailList;
  double purchaseAmount;

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

  PersonData person1(fName, lName, addr, givenCity, givenState, zipCode,
                     phoneNum);

  CustomerData customer1(person1, customerNum, mailList);

  while (true) {
    cout << "Please input the total purchase amount: ";
    cin >> purchaseAmount;

    if (purchaseAmount > 0)
      break;
    cout << "\nWrong value\n";
  }

  PreferredCustomer preferedCustomer1(customer1, purchaseAmount);

  cout << "He or she gets a " << preferedCustomer1.getDiscountLevel()
       << "% discount on all future purchases.";
}
```