# OOP-Based-System-Design

## AIM:
To design and implement an Online Course Management System using Object-Oriented Programming (OOP) principles, demonstrating core concepts such as abstraction, inheritance, encapsulation, and polymorphism.

## PROCEDURE:
### 1.Design UML Diagram:
    Create a class diagram showing relationships between User, Student, Instructor, Course, Assignment, and Grade.

### 2.Define Classes in JavaScript:
    Implement each class with constructors, methods, and properties.
    Use:

        Inheritance (Student, Instructor from User)

        Encapsulation (getters/setters)

        Polymorphism (method overriding like login())
        
### 3.Implement Functionalities:

        Instructor creates a course and assignments

        Student enrolls and submits assignments

        Instructor assigns grades
        
### 4.Test Scenarios:

        Create users, enroll students, upload assignments, and assign grades

        Output results to verify class interaction

  ## PROGRAM:
  JavaScript OOP code with the following structure:
  
    Classes: User, Student, Instructor, Course, Assignment, Grade

    Features: Course creation, enrollment, assignment submission, grading

```js
class User {
    constructor(id, name, email) {
        this._id = id;
        this._name = name;
        this._email = email;
    }

    login() {
        console.log(`${this._name} has logged in.`);
    }

    get name() {
        return this._name;
    }

    set name(newName) {
        this._name = newName;
    }
}

class Student extends User {
    constructor(id, name, email) {
        super(id, name, email);
        this.enrolledCourses = [];
        this.grades = [];
    }

    enroll(course) {
        course.enroll(this);
        this.enrolledCourses.push(course);
    }

    viewGrades() {
        return this.grades.map(grade => `${grade.assignment.title}: ${grade.getGrade()}`);
    }
}

class Instructor extends User {
    constructor(id, name, email) {
        super(id, name, email);
        this.createdCourses = [];
    }

    createCourse(title, description) {
        const course = new Course(title, description, this);
        this.createdCourses.push(course);
        return course;
    }

    gradeAssignment(assignment, student, score) {
        const grade = new Grade(student, assignment, score);
        student.grades.push(grade);
        return grade;
    }
}

class Course {
    constructor(title, description, instructor) {
        this.title = title;
        this.description = description;
        this.instructor = instructor;
        this.students = [];
        this.assignments = [];
    }

    enroll(student) {
        this.students.push(student);
    }

    addAssignment(title, dueDate) {
        const assignment = new Assignment(title, dueDate);
        this.assignments.push(assignment);
        return assignment;
    }
}

class Assignment {
    constructor(title, dueDate) {
        this.title = title;
        this.dueDate = dueDate;
        this.submissions = new Map();
    }

    submit(student, content) {
        this.submissions.set(student.name, content);
    }
}

class Grade {
    constructor(student, assignment, score) {
        this.student = student;
        this.assignment = assignment;
        this.score = score;
    }

    getGrade() {
        return this.score;
    }
}

```


## OUTPUT:
<img width="1024" height="1536" alt="a585855d-5823-471b-8cbb-65b0d377202b-1" src="https://github.com/user-attachments/assets/8ca1efdf-723c-4060-9016-d6ccbb95c415" />

## RESULT:
A working OOP-based simulation of an Online Course Management System that showcases the use of OOP and SOLID principles, demonstrating design thinking, scalability, and clean architecture.
