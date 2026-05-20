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
<img width="1312" height="923" alt="image" src="https://github.com/user-attachments/assets/dc29e36c-bf94-456c-9484-f32fe09935b0" />


### Entities and Attributes

Entity       | Attributes (PK, FK)                                  | Notes
------------ | ---------------------------------------------------- | -----------------------------------------
Customer     | Customer_ID (PK), Name                               | Stores customer details
Reservation  | Reservation_ID (PK), Date, Time,
             | No_of_Guests, Customer_ID (FK)                       | Stores reservation details
Table        | Table_ID (PK), Capacity                              | Stores table information
Order        | Order_ID (PK)                                        | Stores order details
Dish         | Dish_ID (PK), Name, Price                            | Stores dish information
Category     | Category_ID (PK), Name                               | Stores dish categories
Bill         | Receipt_ID (PK), Amount_Total                        | Stores billing details
Waiter       | Waiter_ID (PK), Name                                 | Stores waiter details

### Relationships and Constraints

Relationship                 | Cardinality | Participation | Notes
---------------------------- | ----------- | ------------- | -----------------------------------------------
Customer → Reservation       | 1 : N       | Total         | One customer can make many reservations
Reservation → Table          | 1 : N       | Partial       | One reservation can reserve many tables
Reservation → Order          | 1 : M       | Total         | One reservation can contain many orders
Category → Dish              | 1 : N       | Total         | One category contains many dishes
Waiter → Bill                | 1 : N       | Partial       | One waiter handles many bills
Reservation → Bill           | 1 : 1       | Total         | Each reservation generates one bill
Order → Waiter               | M : N       | Partial       | Many orders can be served by many waiters

### Assumptions
- One customer can make multiple reservations.
- Each dish belongs to one category only.
- Each reservation generates one bill.

---

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
<img width="1285" height="915" alt="image" src="https://github.com/user-attachments/assets/2f8cba47-df75-4dbb-8171-eeee418dfeda" />


### Entities and Attributes

Entity       | Attributes (PK, FK)                                  | Notes
------------ | ---------------------------------------------------- | -----------------------------------------
Member       | Member_ID (PK), Name, Membership_Type, Start_Date    | Stores member details
Programme    | Programme_Name (PK), Programme_Slot                  | Stores programme information
Trainer      | Trainer_ID (PK), Trainer_Name                        | Stores trainer details
Payment      | Payment_ID (PK), Membership, Date, Member_ID (FK)    | Stores payment records
Session      | Session_ID (PK), Session_Slot, Members, Trainers,
             | Session_Date, Time                                   | Stores session details
Attendance   | Attendance_ID (PK), Status, Percentage,
             | Session_ID (FK)                                      | Stores attendance details

### Relationships and Constraints

Relationship                 | Cardinality | Participation | Notes
---------------------------- | ----------- | ------------- | -----------------------------------------
Member → Payment             | 1 : N       | Total         | One member can make many payments
Member → Programme           | 1 : N       | Total         | One member can join many programmes
Programme → Trainer          | N : 1       | Partial       | Many programmes are conducted by one trainer
Member → Session             | N : M       | Partial       | Members can attend many sessions
Trainer → Session            | 1 : N       | Partial       | One trainer handles many sessions
Session → Attendance         | 1 : 1       | Total         | Each session has one attendance record

### Assumptions
- One member can join multiple programmes.
- One trainer can conduct many sessions.
- Members can make multiple payments.
---

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
<img width="1292" height="876" alt="image" src="https://github.com/user-attachments/assets/9c6baa88-abcf-465c-bacb-b407fa68db47" />


### Entities and Attributes

Entity       | Attributes (PK, FK)                                  | Notes
------------ | ---------------------------------------------------- | -----------------------------------------
Customer     | Customer_ID (PK), Name                               | Stores customer details
Reservation  | Reservation_ID (PK), Customer_ID (FK), Date,
             | Time, No_of_Guests                                   | Reservation information
DiningTable  | Table_ID (PK), Capacity, Reservation_ID (FK)         | Table allocation details
Category     | Category_ID (PK), Name                               | Dish categories
Dish         | Dish_ID (PK), Name, Price, Category_ID (FK)          | Menu dish details
Orders       | Order_ID (PK), Reservation_ID (FK), Table_ID (FK)    | Order information
Waiter       | Waiter_ID (PK), Name                                 | Waiter details
Bill         | Receipt_ID (PK), Amount_Total,
             | Reservation_ID (FK), Waiter_ID (FK)                  | Billing information

### Relationships and Constraints

Relationship                 | Cardinality | Participation | Notes
---------------------------- | ----------- | ------------- | -----------------------------------------------
Customer → Reservation       | 1 : N       | Total         | One customer can make many reservations
Reservation → DiningTable    | 1 : N       | Partial       | One reservation can reserve many tables
Category → Dish              | 1 : N       | Total         | One category contains many dishes
Reservation → Orders         | 1 : M       | Total         | One reservation can have many orders
Waiter → Bill                | 1 : N       | Partial       | One waiter handles many bills
Reservation → Bill           | 1 : 1       | Total         | Each reservation generates one bill
### Assumptions
- One member can borrow multiple books.
- One author can write many books.
-Each issued book belongs to one member.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
