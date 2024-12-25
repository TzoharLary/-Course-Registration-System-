
# Course Registration System

A Java-based system for registering users, creating courses, and managing enrollments with real-time waitlist updates. This project demonstrates various design patterns to ensure data integrity, modularity, and efficient course management.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Design Patterns](#design-patterns)
- [Usage](#usage)

## Overview
This system provides a single point of interaction (Singleton) to manage student registrations, create and update courses, and handle waitlists. It ensures that every part of the application (users, courses, observers) communicates through one centralized facade, improving consistency and modularity.

## Features
- **Single Registration System**: Ensures all operations go through a single instance (`RegistrationSystem`)  
- **User Management**: Create students, TAs, and lecturers via the `UserFactory`  
- **Course Management**: Avoids duplicate courses with a Flyweight (`Course` cache)  
- **Real-Time Updates**: Uses the Observer pattern to notify students when a course spot opens  
- **Encapsulation**: `UsersDB` and `CoursesDB` hide internal data structures, providing a simple interface

## Design Patterns
- **Singleton**: `RegistrationSystem` provides a single instance for all registration operations  
- **Factory**: `UserFactory` creates different user types (Student, TA, Lecturer) based on input flags  
- **Flyweight**: `Course` objects are stored and reused to prevent duplicates  
- **Observer**: `StudentObserver` receives notifications when a spot becomes available in a course  
- **Facade**: Multiple layers (e.g., `Student` methods, `RegistrationSystem`) simplify interactions for the user

## Usage
- **Create Users**: Use `UserFactory` to create `Student`, `TA`, or `Lecturer`.
- **Register Courses**: Add new courses through `RegistrationSystem.addCourse()`.
- **Enroll Students**: `RegistrationSystem.RegisterUserToCourse(student, course)`.
- **Waitlist Mechanism**: If a course is full, the student is automatically placed in a waitlist (`StudentObserver`).
- **Removal**: Remove a user from a course (`RegistrationSystem.removeUserFromCourse()`), automatically notifies a waitlisted student if space becomes available.
