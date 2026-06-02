# BudgetNest - Personal Expense Tracker

## Overview

BudgetNest is a Django-based web application designed to help families and individuals manage their income and expenses efficiently. The application provides user authentication, family member management, expense tracking, and report generation features to simplify personal financial management.

---

## Problem Statement

Many families still track expenses manually using notebooks or spreadsheets. This approach makes it difficult to monitor spending patterns, analyze expenses, and generate reports.

BudgetNest addresses this problem by providing a centralized platform to record income and expenses, track spending habits, and generate financial reports automatically.

---

## Tech Stack

### Backend

* Python
* Django 5.2
* Django ORM
* SQLite3

### Frontend

* HTML
* CSS
* Bootstrap 4

### Authentication

* Django Built-in Authentication System
* Session-Based Login and Logout

---

## Features

### 1. Authentication Module

#### Functionality

* User Registration
* User Login
* User Logout
* Session Management

#### Concepts Used

* Django User Model
* Authentication Middleware
* Sessions
* Password Hashing

---

### 2. Family Member Management Module

#### Functionality

* Add Family Members
* Update Member Details
* Delete Members
* View Members List

#### Example

| Name   | Age | Income |
| ------ | --- | ------ |
| Father | 52  | 70000  |
| Mother | 45  | 40000  |

#### Concepts Used

* Django Models
* Model Forms
* CRUD Operations
* ForeignKey Relationships

---

### 3. Expense Tracking Module

#### Functionality

* Add Expenses
* Update Expenses
* Delete Expenses
* Assign Expenses to Family Members
* Track Expense Amount, Purpose, and Date

#### Example

| Member | Purpose | Amount | Date       |
| ------ | ------- | ------ | ---------- |
| Father | Grocery | 2500   | 2026-04-10 |

#### Concepts Used

* ForeignKey Relationships
* Query Filtering
* Django ORM Queries
* Date Handling

---

### 4. Reporting Module

#### Functionality

* Monthly Expense Reports
* Yearly Expense Reports
* Total Expense Dashboard

#### Concepts Used

* Aggregate Functions
* ORM Filtering
* Date-Based Queries
* Context Data Rendering

---

## Database Design

### Relationship Structure

User → FamilyMember → Expense

### FamilyMember Model

```python
class FamilyMember(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE)
    name = models.CharField(max_length=100)
    age = models.IntegerField()
    income = models.FloatField()
```

### Expense Model

```python
class Expense(models.Model):
    member = models.ForeignKey(FamilyMember, on_delete=models.CASCADE)
    purpose = models.CharField(max_length=200)
    amount = models.FloatField()
    date = models.DateField()
```

---

## Django Concepts Used

### MVT Architecture

* Model
* View
* Template

### ORM

Example:

```python
Expense.objects.filter(date__year=2026)
```

### Forms

* Django Forms
* CSRF Protection
* Form Validation

### Templates

* Template Inheritance
* Bootstrap Integration

### URL Routing

```python
path('expenses/', views.expense_list)
```

### Authentication

* login_required
* authenticate()
* login()
* logout()

---

## Challenges Faced

### Challenge 1: User-Specific Data Filtering

Initially, all users could view every expense record. This issue was resolved by filtering data based on the logged-in user.

```python
Expense.objects.filter(member__user=request.user)
```

### Challenge 2: Dynamic Report Generation

Generating monthly and yearly reports dynamically was challenging at first. This was solved using Django ORM date filters and aggregation queries.

---

## Security Features

* CSRF Protection
* Session Authentication
* Login Required Pages
* Password Hashing
* User-Specific Data Access Control

---

## Future Enhancements

* Add Interactive Charts using Chart.js
* Export Reports to PDF and Excel
* Build REST APIs using Django REST Framework
* Add Overspending Notifications
* Deploy on AWS or Google Cloud Platform

---

## Learning Outcomes

This project provided practical experience with:

* Django CRUD Operations
* User Authentication and Authorization
* Django ORM Queries
* Template Rendering
* Report Generation
* Relational Database Design
* User-Specific Data Management

---

## Conclusion

BudgetNest is a complete personal expense management system that helps users organize financial data, monitor spending habits, and generate useful reports. The project strengthened my understanding of real-world web application development using Django and relational databases.
