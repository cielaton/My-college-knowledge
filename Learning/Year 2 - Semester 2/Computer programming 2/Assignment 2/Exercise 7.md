```cpp
#include <iostream>

using namespace std;

// ParkedCar
class ParkedCar {
private:
  string make, model, color, license;
  int parkedTime;

public:
  ParkedCar(string, string, string, string, int);

  string getMake();
  string getModel();
  string getColor();
  string getLicense();
  int getParkedTime();
};

ParkedCar::ParkedCar(string carsMake, string carsModel, string carsColor,
                     string carsLicense, int carsParkedTime) {
  make = carsMake;
  model = carsModel;
  color = carsColor;
  license = carsLicense;
  parkedTime = carsParkedTime;
}

string ParkedCar::getMake() { return make; }
string ParkedCar::getModel() { return model; }
string ParkedCar::getColor() { return color; }
string ParkedCar::getLicense() { return license; }
int ParkedCar::getParkedTime() { return parkedTime; }

// ParkingMeter
class ParkingMeter {
private:
  int purchasedParkingTime = 0;

public:
  ParkingMeter(int);
  int getPurchasedParkingTime();
};

ParkingMeter::ParkingMeter(int time) { purchasedParkingTime = time; }
int ParkingMeter::getPurchasedParkingTime() { return purchasedParkingTime; }

// ParkingTicket
class ParkingTicket {
private:
  const int fineForFirstHour = 25;
  const int fineForAdditionalHours = 10;

public:
  ParkingTicket(ParkedCar parkedCar, ParkingMeter parkingMeter,
                string officerName, int officeBadgeNumber) {
    cout << "Make: " << parkedCar.getMake() << endl;
    cout << "Model: " << parkedCar.getModel() << endl;
    cout << "Color: " << parkedCar.getColor() << endl;
    cout << "License number: " << parkedCar.getLicense() << "\n\n";

    int illegalParkedTime =
        parkedCar.getParkedTime() - parkingMeter.getPurchasedParkingTime();
    cout << "Your fine is: "
         << fineForFirstHour + (illegalParkedTime - 1) * fineForAdditionalHours
         << "\n\n";

    cout << "Response officer: " << officerName << endl
         << "Badge number: " << officeBadgeNumber;
  }
};

// PoliceOfficer
class PoliceOfficer {
private:
  string name;
  int badgeNumber;

public:
  PoliceOfficer(string, int);

  string getName();
  int getBadgeNumber();

  void determineExpiredParkingTime(ParkedCar, ParkingMeter);
};

PoliceOfficer::PoliceOfficer(string officerName, int officeBadgeNumber) {
  name = officerName;
  badgeNumber = officeBadgeNumber;
}

string PoliceOfficer::getName() { return name; }
int PoliceOfficer::getBadgeNumber() { return badgeNumber; }

void PoliceOfficer::determineExpiredParkingTime(ParkedCar car,
                                                ParkingMeter meter) {
  if (car.getParkedTime() > meter.getPurchasedParkingTime()) {
    cout << "Your car is illegaly parked." << endl;
    ParkingTicket ticket(car, meter, name, badgeNumber);
  }
}

int main() {
  ParkedCar car = ParkedCar("Ford", "Ford Exploer", "Red", "1234A", 3);
  ParkingMeter purchased(2);
  PoliceOfficer randomOfficer("Steve", 1234);
  randomOfficer.determineExpiredParkingTime(car, purchased);
}
```