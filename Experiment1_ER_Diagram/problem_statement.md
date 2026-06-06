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
![ER Diagram]

<img width="963" height="535" alt="image" src="https://github.com/user-attachments/assets/2aacb982-401c-4320-9b14-aaf0b5cf1f05" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|---------------------|-------|
| Member | MemberID (PK), Name, StartDate | Members registered at the gym |
| Trainer | TrainerID (PK), Name, Qualification | Trainers at the gym |
| Program | ProgramID (PK), ProgramName, Category | Fitness programs offered |
| Session | SessionID (PK) | Training sessions conducted |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|----------------|-------|
| Member to Join | M:N | Partial on both sides | Members join trainers for programs |
| Trainer to Conducts | 1:N | Total on Trainer side | Trainers conduct multiple sessions |
| Session to Records | M:N | Total on Session side | Sessions record attendance and payments |
| Session to Attendance | 1:N | Total on Session side | Each session has multiple attendance records |
| Session to Payment | 1:N | Total on Session side | Each session may have payment records |

### Assumptions
- Members can join multiple trainers for different programs
- Each trainer conducts one or more sessions
- Sessions are conducted by trainers and recorded in programs
- Attendance and payments are tracked per session
- A session generates both attendance and payment records

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
*Paste or attach your diagram here*  
![ER Diagram]

<img width="484" height="549" alt="image" src="https://github.com/user-attachments/assets/4f3e4ba5-ddce-4738-9755-3335fcb5ed6c" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|---------------------|-------|
| Member | MemberID (PK), Name, MembershipType, StartDate, Email, PhoneNumber | Library members |
| Book | ISBN (PK), Title, Author, Category, PublicationYear | Books in library inventory |
| Loan | LoanID (PK), LoanDate, DueDate, ReturnDate, FineAmount | Book loan records |
| Room | RoomID (PK), RoomName, Capacity, Purpose | Rooms for events and study |
| Booking | BookingID (PK), BookingDate, StartTime, EndTime, RoomID (FK), MemberID (FK) | Room bookings by members |
| Speaker | SpeakerID (PK), Name, Bio, Credentials | Guest speakers or authors |
| Event | EventID (PK), Name, Description, StartTime, EndTime, RoomID (FK) | Cultural events organized |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|----------------|-------|
| Member to Loan | 1:N | Total on Member side; Partial on Loan side | Members borrow multiple books; loans are optional |
| Book to Loan | 1:N | Total on Book side; Partial on Loan side | Books can be loaned multiple times; some never borrowed |
| Member to Booking | 1:N | Total on Member side; Partial on Booking side | Members book rooms multiple times; bookings optional |
| Room to Booking | 1:N | Total on Room side; Partial on Booking side | Rooms host multiple bookings; may be unbooked |
| Member to Event Registration | M:N | Partial on both sides | Members register for multiple events |
| Event to Event Helper | M:N | Total on Event side | Events have speakers and helpers |
| Speaker to Event Helper | 1:N | Total on Speaker side; Partial on Event Helper side | Speakers appear at multiple events |
| Event to Room | M:1 | Total on Event side; Partial on Room side | Each event uses one room |

### Assumptions
- Members can book rooms for different purposes and times
- Loan records include fine amounts for overdue books
- Events are held in specific rooms with scheduled times
- Speakers and event helpers are tracked separately
- Room capacity must be validated for event attendance
- Members can register for multiple events

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
*Paste or attach your diagram here*  
![ER Diagram]

<img width="623" height="395" alt="image" src="https://github.com/user-attachments/assets/6003a599-82d7-40de-98a9-c73ebde57e4e" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|---------------------|-------|
| Chef | ChefID (PK), ChefName, ChefSalary | Kitchen staff members |
| Meal | MealID (PK), MealName, MealPrice, Attribute | Menu items offered |
| Supplier | SupplierID (PK), SupplierName, SupplierCity | Food suppliers |
| Ingredients | IngredientID (PK), IngredientName, Description | Meal ingredients |
| Customers | CustomerID (PK), CustomerAddress, CustomerName, CustomerPhone | Restaurant customers |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|----------------|-------|
| Chef to Prepares | 1:N | Total on Chef side; Partial on Meal side | Chefs prepare multiple meals; meals may not be prepared yet |
| Customers to Orders | M:N | Total on Customers side; Partial on Orders side | Customers place multiple orders; orders are optional |
| Meal to Orders | 1:N | Total on Meal side; Partial on Orders side | Meals can be ordered multiple times; some never ordered |
| Meal to Consists Of | 1:N | Total on Meal side; Partial on Consists Of side | Meals contain multiple ingredients; ingredients may not be used |
| Ingredients to Consists Of | 1:N | Total on Ingredients side; Partial on Consists Of side | Ingredients appear in multiple meals |
| Supplier to Attends | M:N | Total on Supplier side; Partial on Attends side | Suppliers provide multiple ingredients; attend customer orders |
| Customers to Attends | M:N | Partial on both sides | Customers may attend events; not all customers attend |

### Assumptions
- Each meal is prepared by one or more chefs
- Customers can order multiple meals in a single transaction
- Meals consist of multiple ingredients sourced from suppliers
- Suppliers provide ingredients and may attend customer orders
- Chef salary is stored separately from meal pricing
- Customer address and phone are tracked for delivery/contact purposes
- Ingredient descriptions detail preparation or storage requirements

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
