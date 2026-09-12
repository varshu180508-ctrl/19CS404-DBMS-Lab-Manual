# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
*Paste or attach your diagram here*  
<img width="887" height="718" alt="Screenshot 2026-08-04 101151" src="https://github.com/user-attachments/assets/560ce7dc-096c-41ec-896d-393e5da00eec" />



### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|---------------------|-------|
| MEMBER | Member_ID (PK), Name, Membership_Type, Start_Date | Stores member registration details. |
| PROGRAM | Program_ID (PK), Program_Name | Stores gym programs such as Yoga, Zumba, and Weight Training. |
| TRAINER | Trainer_ID (PK), Trainer_Name | Stores trainer details. |
| MEMBER_PROGRAM | Member_ID (PK, FK), Program_ID (PK, FK) | Represents the programs joined by each member. |
| PROGRAM_TRAINER | Program_ID (PK, FK), Trainer_ID (PK, FK) | Represents trainers assigned to each program. |
| SESSION | Session_ID (PK), Member_ID (FK), Trainer_ID (FK), Session_Date, Session_Time | Stores personal training session details. |
| ATTENDANCE | Attendance_ID (PK), Member_ID (FK), Session_ID (FK), Attendance_Date, Status | Records attendance for each session. |
| PAYMENT | Payment_ID (PK), Member_ID (FK), Session_ID (FK), Amount, Payment_Date, Payment_Type | Tracks payments for memberships and sessions. |

### Relationships and Constraints


| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| MEMBER — PROGRAM | M : N | Partial | A member can join multiple programs, and a program can have multiple members. |
| PROGRAM — TRAINER | M : N | Partial | A program can have multiple trainers, and a trainer can be assigned to multiple programs. |
| MEMBER — SESSION | 1 : M | Total for SESSION | A member can book multiple personal training sessions. |
| TRAINER — SESSION | 1 : M | Total for SESSION | A trainer can conduct multiple personal training sessions. |
| MEMBER — PAYMENT | 1 : M | Total for PAYMENT | A member can make multiple payments for memberships and sessions. |
| SESSION — PAYMENT | 1 : 0..1 | Partial for PAYMENT | A session may or may not have a payment. |

### Assumptions

- Each member has a unique Member_ID.
- Each program has a unique Program_ID.
- Each trainer has a unique Trainer_ID.
- A member can join multiple programs.
- A program can have multiple members.
- A program can be assigned to multiple trainers.
- A trainer can be assigned to multiple programs.
- Each personal training session is booked by one member and conducted by one trainer.
- Attendance is recorded for each training session.
- A member can make multiple payments for memberships and training sessions.
- A payment may be associated with a membership or a personal training session.
- Membership type and start date are recorded during member registration.

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
<img width="1027" height="737" alt="Screenshot 2026-08-04 101239" src="https://github.com/user-attachments/assets/789143d9-e6ae-4df8-bf1d-d0f9ab6d4744" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| MEMBER | Member_ID (PK), Name | Stores library member details. |
| BOOK | Book_ID (PK), Title, Author, Category | Stores book details. |
| LOAN | Loan_ID (PK), Member_ID (FK), Book_ID (FK), Loan_Date, Return_Date | Tracks book borrowing and return details. |
| EVENT | Event_ID (PK), Event_Name, Event_Date | Stores library event details. |
| SPEAKER | Speaker_ID (PK), Speaker_Name | Stores speaker or author details. |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| MEMBER — LOAN | 1 : M | Total for LOAN | A member can borrow multiple books. |
| BOOK — LOAN | 1 : M | Total for LOAN | A book can be borrowed multiple times over time. |
| MEMBER — EVENT | M : N | Partial | A member can register for multiple events, and an event can have multiple members. |
| EVENT — SPEAKER | M : N | Total for EVENT | An event can have one or more speakers, and a speaker can participate in multiple events. |
| LOAN — FINE | 1 : 0..1 | Partial for FINE | A loan may or may not have an overdue fine. |
| EVENT — ROOM | M : N | Partial | Events can require rooms, and rooms can be booked for multiple events. |

## Assumptions

- Each member has a unique Member_ID.
- Each book has a unique Book_ID.
- A member can borrow multiple books.
- A book can be borrowed multiple times by different members over time.
- Each loan records the loan date and return date.
- A member can register for multiple events.
- Each event has one or more speakers/authors.
- A speaker can participate in multiple events.
- Rooms can be booked multiple times for different events or study purposes.
- A fine is generated only when a book is returned after the due date.
- A loan may have zero or one overdue fine.

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="1280" height="838" alt="ER3" src="https://github.com/user-attachments/assets/e7f6a0e3-ed09-429b-b163-52137cea29c7" />



### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| CUSTOMER | Customer_ID (PK), Name, Phone | Stores customer details. |
| RESERVATION | Reservation_ID (PK), Customer_ID (FK), Reservation_Date, Reservation_Time, Number_of_Guests, Reservation_Type | Stores reservation and walk-in details. |
| ORDER | Order_ID (PK), Reservation_ID (FK), Order_Date, Order_Time | Stores food orders linked to reservations. |
| DISH | Dish_ID (PK), Category_ID (FK), Dish_Name, Price | Stores dish details and prices. |
| CATEGORY | Category_ID (PK), Category_Name | Stores dish categories such as Starter, Main, and Dessert. |
| ORDER_ITEM | Order_ID (PK, FK), Dish_ID (PK, FK), Quantity | Connects orders with multiple dishes. |
| BILL | Bill_ID (PK), Reservation_ID (FK), Food_Charge, Service_Charge, Total_Amount | Stores bill details for each reservation. |
| WAITER | Waiter_ID (PK), Waiter_Name | Stores waiter details. |
| RESERVATION_WAITER | Reservation_ID (PK, FK), Waiter_ID (PK, FK) | Connects waiters with reservations they serve. |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| CUSTOMER — RESERVATION | 1 : M | Partial for CUSTOMER, Total for RESERVATION | A customer can make multiple reservations or walk-ins. |
| RESERVATION — ORDER | 1 : M | Partial for RESERVATION, Total for ORDER | A reservation can have multiple food orders. |
| ORDER — ORDER_ITEM | 1 : M | Total for ORDER_ITEM | Each order contains multiple dishes. |
| DISH — ORDER_ITEM | 1 : M | Partial for DISH, Total for ORDER_ITEM | A dish can appear in multiple orders. |
| CATEGORY — DISH | 1 : M | Total for DISH | A category can contain multiple dishes. |
| RESERVATION — BILL | 1 : 1 | Total for BILL | Each reservation generates one bill. |
| RESERVATION — WAITER | M : N | Partial | A reservation can be served by waiters, and a waiter can serve multiple reservations. |

### Assumptions
- Each customer can make multiple reservations or walk in.
- Each reservation is associated with one customer and contains date, time, and number of guests.
- Each order can contain multiple dishes, and each dish belongs to one category.
- Each reservation generates one bill including food and service charges.
- Waiters can be assigned to multiple reservations.

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
