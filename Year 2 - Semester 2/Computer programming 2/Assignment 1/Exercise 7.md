#### Class initialization:
```cpp
#include <string>
#include <iostream>

using namespace std;

void freezingMessage(string substance) {
  cout << substance << " willl freeze at this temperature\n";
}

void boilingMessage(string substance) {
  cout << substance << " willl boil at this temperature\n";
}

class Substances {
private:
  long temperature;

public:
  Substances(long);
  void setName(string);
  void setTemperature(long);

  string getName() const;
  long getTemperature() const;

  bool isEthyFreezing() const { return temperature <= -173 ? true : false; }
  bool isEthyBoiling() const { return temperature >= 172 ? true : false; }

  bool isOxygenFreezing() const { return temperature <= -362 ? true : false; }
  bool isOxygenBoiling() const { return temperature >= -306 ? true : false; }

  bool isWaterFreezing() const { return temperature <= 32 ? true : false; }
  bool isWaterBoiling() const { return temperature >= 212 ? true : false; }
};

Substances::Substances(long temp) {
  temperature = temp;
  if (Substances::isEthyFreezing())
    freezingMessage("Ethy");
  if (Substances::isEthyBoiling())
    boilingMessage("Ethy");
  if (Substances::isOxygenFreezing())
    freezingMessage("Oxygen");
  if (Substances::isOxygenBoiling())
    boilingMessage("Oxygen");
  if (Substances::isWaterFreezing())
    freezingMessage("Water");
  if (Substances::isWaterBoiling())
    boilingMessage("Water");
}

void Substances::setTemperature(long temp) { temperature = temp; }

long Substances::getTemperature() const { return temperature; }

```

#### Main program:
```cpp
#include <iostream>

using namespace std;

int main() {
  long temp;
  cout << "PLease input a temperature: ";
  cin >> temp;

  Substances substance(temp);
}
```