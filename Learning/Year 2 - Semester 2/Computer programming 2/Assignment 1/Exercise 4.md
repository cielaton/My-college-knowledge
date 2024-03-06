#### Class initialization:
```cpp
class RetailItem {
private:
  int itemNumber;
  int quantity;
  double cost;
  double totalCost;

public:
  RetailItem();
  RetailItem(int, int, double);

  void setItemNumber(int);
  void setQuantity(int);
  void setCost(double);
  void setTotalCost(double);

  int getItemNumber() const;
  int getQuantity() const;
  double getCost() const;
  double getTotalCost() const;
};

RetailItem::RetailItem(int item, int quantity, double cost) {
  itemNumber = item;
  quantity = quantity;
  cost = cost;
}

void RetailItem::setItemNumber(int item) { itemNumber = item; }
void RetailItem::setQuantity(int quantity) { quantity = quantity; }
void RetailItem::setCost(double cost) { cost = cost; }
void RetailItem::setTotalCost(double totalCost) { totalCost = totalCost; }

int RetailItem::getItemNumber() const { return itemNumber; }
int RetailItem::getQuantity() const { return quantity; }
double RetailItem::getCost() const { return cost; }
double RetailItem::getTotalCost() const { return totalCost; }
```

#### Main program:
```cpp
#include <iostream>

using namespace std;

int main() {}
```