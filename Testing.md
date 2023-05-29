GradedActivity class:
```cpp
#ifndef GRADEDACTIVITY_H
#define GRADEDACTIVITY_H

class GradedActivity {
private:
  double score;

public:
  GradedActivity() { score = 0.0; }

  GradedActivity(double s) { score = s; }

  void setScore(double s) { score = s; }

  double getScore() const { return score; }

  char getLetterGrade() {
    char letterGrade; // To hold the letter grade
    if (score > 89)
      letterGrade = 'A';
    else if (score > 79)
      letterGrade = 'B';
    else if (score > 69)
      letterGrade = 'C';
    else if (score > 59)
      letterGrade = 'D';
    else
      letterGrade = 'F';
    return letterGrade;
  };
};
#endif

```

The Essay class:
```cpp
#ifndef ESSAY
#define ESSAY

#include "./GradedActivity.h"

class Essay : public GradedActivity {
public:
  Essay(double grammar, double spelling, double correctLength, double content) {
    setScore(grammar + spelling + correctLength + content);
  }
};

#endif

```

In a course, a teacher gives the following tests and assignments:

- A lab activity that is observed by the teacher and assigned a numeric score  
- A pass/fail exam that has 10 questions. The minimum passing score is 70  
- An essay that is assigned a numeric score  
- A final exam that has 50 questions  

Write a class named CourseGrades. The class should have a member named grades that is an array of GradedActivity pointers. The grades array should have four elements, one for each of the assignments previously described. The class should have the following member functions:  

setLab: This function should accept the address of a GradedActivity object as its argument. This object should already hold the student’s score for the lab activity. Element 0 of the grades array should reference this object.  

setPassFailExam: This function should accept the address of a PassFailExam object as its argument. This object should already hold the student’s score for the pass/fail exam. Element 1 of the grades array should reference this object.  

setEssay: This function should accept the address of an Essay object as its argument. (See Problem 4 for the Essay class. If you have not completed Problem 4, use a GradedActivity object instead.) This object should already hold the student’s score for the essay. Element 2 of the grades array should reference this object.  

setFinalExam: This function should accept the address of a FinalExam object as its argument (showed below). This object should already hold the student’s score for the final exam. Element 3 of the grades array should reference this object.  

print: This function should display the numeric scores and grades for each element in the grades array.  

Demonstrate the class in a program.

Write the PassFailExam class, FinalExam class, and the solution for the above problem in cpp, make sure there is no error



PassFailExam class:
```cpp
#ifndef PASSFAILEXAM_H
#define PASSFAILEXAM_H

#include "./GradedActivity.h"

class PassFailExam : public GradedActivity {
private:
  int numQuestions;
  double pointsEach;
  int numMissed;
public:
  PassFailExam(int questions, int missed) {
    numQuestions = questions;
    numMissed = missed;
    pointsEach = 100.0 / questions;
    double numericScore = 100.0 - (missed * pointsEach);
    setScore(numericScore);
  }

  bool pass() const { return getScore() >= 70; }
};

#endif

```

FinalExam class:
```cpp
#ifndef FINALEXAM_H
#define FINALEXAM_H

#include "./GradedActivity.h"

class FinalExam : public GradedActivity {
private:
  int numQuestions;
  double pointsEach;
public:
  FinalExam(int questions, int missed) {
    numQuestions = questions;
    pointsEach = 100.0 / questions;
    double numericScore = 100.0 - (missed * pointsEach);
    setScore(numericScore);
  }
};

#endif

```

CourseGrades class:
```cpp
#ifndef COURSEGRADES_H
#define COURSEGRADES_H

#include "./GradedActivity.h"
#include "./PassFailExam.h"
#include "./Essay.h"
#include "./FinalExam.h"

class CourseGrades {
private:
   GradedActivity* grades[4];

public:

   void setLab(GradedActivity* lab) { grades[0] = lab; }

   void setPassFailExam(PassFailExam* exam) { grades[1] = exam; }

   void setEssay(Essay* essay) { grades[2] = essay; }

   void setFinalExam(FinalExam* finalExam) { grades[3] = finalExam; }

   void print() {
     for (int i = 0; i < 4; i++) {
       std::cout << "Grade " << i+1 << ": ";
       std::cout << grades[i]->getScore() << " (" << grades[i]->getLetterGrade() << ")" << std::endl;
     }
   }

};

#endif

```

Program:
```cpp
#include <iostream>
#include "./CourseGrades.h"

int main() {
  GradedActivity* lab = new GradedActivity(85);
  PassFailExam* passFailExam = new PassFailExam(10, 2);
  Essay* essay = new Essay(20, 15, 18, 25);
  FinalExam* finalExam = new FinalExam(50, 5);

  CourseGrades courseGrades;
  courseGrades.setLab(lab);
  courseGrades.setPassFailExam(passFailExam);
  courseGrades.setEssay(essay);
  courseGrades.setFinalExam(finalExam);

  courseGrades.print();

  delete lab;
  delete passFailExam;
  delete essay;
  delete finalExam;

	return EXIT_SUCCESS;
}
```


