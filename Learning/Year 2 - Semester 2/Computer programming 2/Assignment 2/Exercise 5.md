```cpp
class TimeOff {
private:
  string employeeName;
  int idNumber;
  NumDays maxSickDays, sickTaken, maxVacation, vacTaken, maxUnpaid, unpaidTaken;

public:
  TimeOff();
  TimeOff(string, int, NumDays, NumDays, NumDays, NumDays, NumDays, NumDays);

  void setEmployeeName(string);
  void setIdNumber(int);
  void setMaxSickDays(NumDays);
  void setSickTaken(NumDays);
  void setMaxVacation(NumDays);
  void setVacTaken(NumDays);
  void setMaxUnpaid(NumDays);
  void setUnpaidTaken(NumDays);

  string getEmployeeName();
  int getIdNumber();
  NumDays getMaxSickDays();
  NumDays getSickTaken();
  NumDays getMaxVacation();
  NumDays getVacTaken();
  NumDays getMaxUnpaid();
  NumDays getUnpaidTaken();
};

TimeOff::TimeOff(string name, int id, NumDays maxSickDays, NumDays sickTaken,
                 NumDays maxVacation, NumDays vacTaken, NumDays maxUnpaid,
                 NumDays unpaidTaken) {
  employeeName = name;
  idNumber = id;
  maxSickDays = maxSickDays;
  sickTaken = sickTaken;
  maxVacation = maxVacation;
  vacTaken = vacTaken;
  maxUnpaid = maxUnpaid;
  unpaidTaken = unpaidTaken;
}

void TimeOff::setEmployeeName(string name) { employeeName = name; }
void TimeOff::setIdNumber(int id) { idNumber = id; }
void TimeOff::setMaxSickDays(NumDays maxSickDays) { maxSickDays = maxSickDays; }
void TimeOff::setSickTaken(NumDays sickTaken) { sickTaken = sickTaken; }
void TimeOff::setMaxVacation(NumDays maxVacation) {
  if (maxVacation.getWorkHours() <= 240)
    maxVacation = maxVacation;
  else
    cout << "This value is invalid due to company policy";
}
void TimeOff::setVacTaken(NumDays vacTaken) { vacTaken = vacTaken; }
void TimeOff::setMaxUnpaid(NumDays maxUnpaid) { maxUnpaid = maxUnpaid; }
void TimeOff::setUnpaidTaken(NumDays unpaidTaken) { unpaidTaken = unpaidTaken; }

string TimeOff::getEmployeeName() { return employeeName; }
int TimeOff::getIdNumber() { return idNumber; }
NumDays TimeOff::getMaxSickDays() { return maxSickDays; }
NumDays TimeOff::getSickTaken() { return sickTaken; }
NumDays TimeOff::getMaxVacation() { return maxVacation; }
NumDays TimeOff::getVacTaken() { return vacTaken; }
NumDays TimeOff::getMaxUnpaid() { return maxUnpaid; }
NumDays TimeOff::getUnpaidTaken() { return unpaidTaken; }

```