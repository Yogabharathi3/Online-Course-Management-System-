# Online Course Management System
## Aim:
To design an Online Course Management System using core OOP concepts and demonstrate abstraction, encapsulation, inheritance, and polymorphism through UML and code.
## Task 1:
### Design a UML Class Diagram:
<img width="1919" height="911" alt="image" src="https://github.com/user-attachments/assets/68d33114-5bb6-413a-99e3-6b7c0d3439e2" />

## Task 2:
### Implement or pseudocode the structure in JavaScript:
```
class User {
    constructor(name, email) {
        this.name = name;
        this.email = email;
    }

    login() {
        console.log(`${this.name} logged in.`);
    }

    getRole() {
        return 'User';
    }
}

class Student extends User {
    constructor(name, email, studentID) {
        super(name, email);
        this.studentID = studentID;
        this.courses = [];
    }

    enroll(course) {
        this.courses.push(course);
        course.addStudent(this);
    }

    getRole() {
        return 'Student';
    }
}
class Instructor extends User {
    constructor(name, email, instructorID) {
        super(name, email);
        this.instructorID = instructorID;
    }

    createCourse(title, code) {
        return new Course(title, code, this);
    }

    gradeAssignment(assignment, student, score) {
        assignment.addGrade(new Grade(student, assignment, score));
    }

    getRole() {
        return 'Instructor';
    }
}
class Course {
    constructor(title, code, instructor) {
        this.title = title;
        this.code = code;
        this.instructor = instructor;
        this.students = [];
        this.assignments = [];
    }

    addStudent(student) {
        this.students.push(student);
    }

    addAssignment(assignment) {
        this.assignments.push(assignment);
    }
}
class Assignment {
    constructor(title, dueDate, course) {
        this.title = title;
        this.dueDate = dueDate;
        this.course = course;
        this.grades = [];
    }

    addGrade(grade) {
        this.grades.push(grade);
    }
}
class Grade {
    constructor(student, assignment, score) {
        this.student = student;
        this.assignment = assignment;
        this.score = score;
    }
    getScore() {
        return this.score;
    }

    setScore(newScore) {
        if (newScore >= 0 && newScore <= 100) {
            this.score = newScore;
        } else {
            console.log("Invalid score.");
        }
    }
}
```
## Task 3:
### Explain Your OOP Design:
#### OOP Principles Used
1. Abstraction:
We used abstraction by designing high-level classes like User, Course, and Assignment that hide complex implementation details. For example, User provides a simple login() method without exposing how authentication works internally.

2. Encapsulation:
Private properties (like score, email, studentID) are protected and accessed through public getter/setter methods. This keeps internal data safe and allows validation—for instance, Grade.setScore() only accepts scores between 0 and 100.

3. Inheritance:
The User class is a base class with common attributes and behaviors. Student and Instructor inherit from it, reusing the logic while adding their own methods like enroll() and createCourse(), avoiding code duplication.

4. Polymorphism:
The getRole() method is overridden in Student and Instructor. When getRole() is called on a User reference, the correct version runs based on the actual object type. This makes the system adaptable to different user roles.

#### SOLID Principles 
S – Single Responsibility Principle:
Each class handles one responsibility: User manages user identity, Course handles course data, Grade manages scores.

O – Open/Closed Principle:
The system allows adding new features (like a new user role) without changing existing code—thanks to interfaces and polymorphism.

L – Liskov Substitution Principle:
Anywhere a User is expected, we can safely use a Student or Instructor object without breaking functionality.

I – Interface Segregation Principle:
Each class only contains the methods it needs. There’s no bloated interface forcing unrelated methods onto a class.

D – Dependency Inversion Principle:
While not deeply shown here, the system could rely on abstract User or Switchable-like interfaces, promoting flexibility and testability.
## Result:
The system was successfully modeled with a clear UML diagram and code structure, effectively applying OOP and SOLID principles.
