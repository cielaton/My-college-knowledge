#### Class initialization:
```cpp
int guess;
int total;

class Question {
private:
  string questionText;
  string answer1;
  string answer2;
  string answer3;
  string answer4;
  int correctAnswer;
  int questionScore;

public:
  void setValues(string, string, string, string, string, int, int);

  void askQuestion();
};

void Question::setValues(string question, string a1, string a2, string a3,
                         string a4, int answer, int score) {
  questionText = question;
  answer1 = a1;
  answer2 = a2;
  answer3 = a3;
  answer4 = a4;
  correctAnswer = answer;
  questionScore = score;
}

void Question::askQuestion() {
  cout << endl;

  cout << questionText << endl;
  cout << "1. " << answer1 << endl;
  cout << "2. " << answer2 << endl;
  cout << "3. " << answer3 << endl;
  cout << "4. " << answer4 << endl;
  cout << endl;

  cout << "What is your answer (number)? ";
  cin >> guess;

  if (guess == correctAnswer) {
    cout << "Correct !\n";

    total = total + questionScore;
    cout << "Score = " << questionScore << " out of " << questionScore << "!\n";
    cout << endl;
  } else {
    cout << "Wrong!\n";
    cout << "Score = 0"
         << " out of " << questionScore << "!\n";
    cout << "Correct answer = " << correctAnswer << endl;
  }
}

```

#### Main program
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {

  Question q1;
  Question q2;
  Question q3;
  Question q4;
  Question q5;
  Question q6;
  Question q7;
  Question q8;
  Question q9;
  Question q10;

  // I'm too lazy to think and create 10 questions with 40 answers.
  q1.setValues("Question : ", "Answer 1", "Answer 2", "Answer 3", "Answer 4", 3,
               1);
  q2.setValues("Question : ", "Answer 1", "Answer 2", "Answer 3", "Answer 4", 3,
               1);
  q3.setValues("Question : ", "Answer 1", "Answer 2", "Answer 3", "Answer 4", 3,
               1);
  q4.setValues("Question : ", "Answer 1", "Answer 2", "Answer 3", "Answer 4", 3,
               1);
  q5.setValues("Question : ", "Answer 1", "Answer 2", "Answer 3", "Answer 4", 3,
               1);
  q6.setValues("Question : ", "Answer 1", "Answer 2", "Answer 3", "Answer 4", 3,
               1);
  q7.setValues("Question : ", "Answer 1", "Answer 2", "Answer 3", "Answer 4", 3,
               1);
  q8.setValues("Question : ", "Answer 1", "Answer 2", "Answer 3", "Answer 4", 3,
               1);
  q9.setValues("Question : ", "Answer 1", "Answer 2", "Answer 3", "Answer 4", 3,
               1);
  q10.setValues("Question : ", "Answer 1", "Answer 2", "Answer 3", "Answer 4",
                3, 1);

  string Respond;
  cout << "Player 1 start!\n"
       << "Are you ready? \nyes/no\n";
  cin >> Respond;

  (Respond == "yes") ? cout << "Good Luck!\n" : cout << "Okay Good Bye!\n";

  q1.askQuestion();
  q2.askQuestion();
  q3.askQuestion();
  q4.askQuestion();
  q5.askQuestion();

  cout << "\n--------------------------------------\nPlayer 2 start!\n"
       << "Are you ready? \nyes/no\n";
  cin >> Respond;

  (Respond == "yes") ? cout << "Good Luck!\n" : cout << "Okay Good Bye!\n";

  q6.askQuestion();
  q7.askQuestion();
  q8.askQuestion();
  q9.askQuestion();
  q10.askQuestion();

  cout << "Total Score = " << total;
}
```