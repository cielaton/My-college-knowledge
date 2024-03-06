#### Class initialization:
```cpp
#include <string>
class Coin {
private:
  string sideUp;

public:
  Coin();

  void setSideUp(string);
  string getSideUp() const;
  void toss();
};

Coin::Coin() {
  srand(time(0));
  rand() % 2 ? sideUp = "heads" : sideUp = "tails";
}

void Coin::setSideUp(string side) { sideUp = side; }

string Coin::getSideUp() const { return sideUp; }

void Coin::toss() {
  srand(time(0));
  rand() % 2 ? Coin::setSideUp("heads") : Coin::setSideUp("tails");
}
```

#### Main program:
```cpp
#include <iostream>

using namespace std;

int main() {
  Coin coin;
  int headsTimes = 0, tailsTimes = 0;
  cout << "Initial side: " << coin.getSideUp() << endl;

  for (int i = 0; i < 20; i++) {
    coin.toss();
    (coin.getSideUp() == "heads") ? headsTimes += 1 : tailsTimes += 1;
  }

  cout << "The number of times heads is facing up: " << headsTimes;
  cout << "The number of times tails is facing up: " << tailsTimes;
}
```