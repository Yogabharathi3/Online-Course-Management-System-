# Online Course Management System
## Aim:
To design an Online Course Management System using core OOP concepts and demonstrate abstraction, encapsulation, inheritance, and polymorphism through UML and code.
## Task 2:
#### Implement or pseudocode the structure in JavaScript:
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
#### Explain Your OOP Design
###### Abstraction:
We abstracted common user behavior in the User class, hiding internal details and exposing only needed methods like login() and getRole().
###### Encapsulation:
Properties like score in Grade are accessed through getters and setters to protect internal state and apply validation.
###### Inheritance:
Student and Instructor inherit from the User class, reusing shared functionality while allowing specialization.
###### Polymorphism:
The getRole() method is overridden in both Student and Instructor, demonstrating polymorphism by changing behavior based on the object type.
###### SOLID Principles Followed:
S – Single Responsibility Principle: Each class has one responsibility (e.g., Grade manages scores, Assignment manages submissions).
O – Open/Closed Principle: The system can be extended (e.g., new user roles or features) without modifying existing code.
L – Liskov Substitution Principle: Student and Instructor can be used wherever User is expected.
I – Interface Segregation Principle: Each class uses only what it needs. No unnecessary methods are forced.
D – Dependency Inversion Principle: The code uses abstractions like User rather than depending on specific types.
## Result:
The system was successfully modeled with a clear UML diagram and code structure, effectively applying OOP and SOLID principles.
