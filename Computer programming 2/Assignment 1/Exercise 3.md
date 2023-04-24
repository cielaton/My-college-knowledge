#### Class initialization:
```cpp
class RetailItem {
private:
  string description;
  int unitsOnHand;
  double price;

public:
  RetailItem(string, int, double);

  void setDescription(string);
  void setUnitOnHand(int);
  void setPrice(double);

  string getDescription() const;
  int getUnitOnHand() const;
  double getPrice() const;
};

RetailItem::RetailItem(string des, int unit, double price) {
  description = des;
  unitsOnHand = unit;
  price = price;
}

void RetailItem::setDescription(string des) { description = des; }
void RetailItem::setUnitOnHand(int unit) { unitsOnHand = unit; }
void RetailItem::setPrice(double price) { price = price; }

string RetailItem::getDescription() const { return description; }
int RetailItem::getUnitOnHand() const { return unitsOnHand; }
double RetailItem::getPrice() const { return price; }
```

#### Main program:
```cpp
#include <iostream>

using namespace std;

int main() {
  RetailItem item1("Jacket", 12, 59.95);
  RetailItem item2("Designer Jean", 40, 34.95);
  RetailItem item3("Shirt", 20, 24.95);
}
```