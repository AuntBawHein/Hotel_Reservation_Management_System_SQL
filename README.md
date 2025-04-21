# Hotel Reservation Management System Using SQL  
**By: Me – A Grade 10 Student Learning SQL**

---

## 1. Introduction

Hi! My name is _______________, and I made a fun school project called **Hotel Reservation Management System**. I made this using something called **SQL** (that’s a language used to talk to databases).

This system is like what real hotels use to **book rooms**, **track guests**, **receive payments**, and more!

---

## 2. Scope / Objectives of My Project

Here is what I planned to do in this project:

- I wanted to **create tables** to store information (like people who book rooms, workers, and payments).
- I wanted to **connect all these tables** so they can "talk" to each other.
- I wanted to **put sample data** into the system (so I can test it).
- I wanted to **ask smart questions** using SQL to get useful answers.
- I also wanted to **draw a diagram** (called an ER diagram) that shows how everything connects.

---

## 3. Why Did I Want to Do This Project?

I wanted to do this because I always wondered how hotels **keep track of so many guests**, **rooms**, and **bookings**.

Also, I wanted to **learn more about databases** — how they work and how companies use them. I thought this would be a great way to **practice my SQL skills** and also have fun!

---

## 4. Tools or Technologies I Used

To build this project, I used:

- **SQL** – a language to create tables and ask questions
- **MySQL / SQL Server** – database software to run the SQL
- **GitHub** – to save and share my project
- **Microsoft Word / Google Docs** – to write my report and upload it

---

## 5. Step-by-Step – How I Built It

---

### Step 1: I Made 10 Tables

I first made a plan. These are the things I needed in my hotel:

1. **Clerk** – the people who work at the front desk  
2. **Customer** – the people who book rooms  
3. **Room** – different types of rooms  
4. **Booking** – when a customer books a room  
5. **Guest** – people who stay in the rooms  
6. **Payment** – payment for the booking  
7. **Facility** – services like the pool, gym, spa  
8. **Review** – customer ratings  
9. **Feedback** – customer comments  
10. **ER Diagram** – the map showing how all the tables are linked

---

### Step 2: I Created Tables Using SQL

Here’s an example of how I made a table:

#### Customer Table

```sql
CREATE TABLE Customer(
    Cus_id INT PRIMARY KEY,
    Cus_firstname VARCHAR(100),
    Cus_lastname VARCHAR(100),
    Cus_age INT,
    Cus_gender VARCHAR(100),
    Cus_nationality VARCHAR(100),
    Cus_email VARCHAR(100),
    Cus_address VARCHAR(100),
    Cus_phone_number VARCHAR(100),
    Cus_password_number VARCHAR(100)
);
```

I did the same for all other tables like Clerks, Rooms, Bookings, etc.

---

### Step 3: I Added Sample Data

Then I added fake information to test it.

#### Example: Add a Customer

```sql
INSERT INTO Customer(Cus_id, Cus_firstname, Cus_lastname, Cus_age, Cus_gender, Cus_nationality, Cus_email, Cus_address, Cus_phone_number, Cus_password_number)
VALUES (1, 'Emma', 'Johnson', 28, 'Female', 'USA', 'emma.johnson@email.com', '123 Main Street', '123-456-7890', 'password123');
```

I added:
- 10 Clerks
- 10 Customers
- 10 Rooms
- 10 Bookings
- 10 Guests
- 10 Payments
- 10 Facilities
- 10 Reviews
- 10 Feedback entries

---

### 🔹 Step 4: I Asked Smart Questions with SQL

Now that everything was connected, I could ask questions like:

#### ✅ Q1: Who booked a room and did they pay?
```sql
SELECT Customer.Cus_firstname, Room.Room_type, Payment.Payment_status
FROM Booking
JOIN Customer ON Booking.Cus_id = Customer.Cus_id
JOIN Room ON Booking.Room_id = Room.Room_id
LEFT JOIN Payment ON Booking.Bk_id = Payment.Booking_id;
```

#### ✅ Q2: Show only customers who paid
```sql
SELECT Customer.Cus_firstname, Room.Room_type, Payment.Payment_status
FROM Booking
JOIN Customer ON Booking.Cus_id = Customer.Cus_id
JOIN Room ON Booking.Room_id = Room.Room_id
JOIN Payment ON Booking.Bk_id = Payment.Booking_id
WHERE Payment.Payment_status = 'Successful';
```

#### ✅ Q3: Which guest stayed in which room?
```sql
SELECT Room.Room_type, Guest.Guest_firstname
FROM Room
JOIN Booking ON Room.Room_id = Booking.Room_id
JOIN Guest ON Booking.Bk_id = Guest.Booking_id;
```

#### ✅ Q4: How many bookings did each customer make?
```sql
SELECT Customer.Cus_firstname, COUNT(Booking.Bk_id) AS Total_Bookings
FROM Customer
LEFT JOIN Booking ON Customer.Cus_id = Booking.Cus_id
GROUP BY Customer.Cus_firstname;
```

#### ✅ Q5: Which rooms have never been booked?
```sql
SELECT Room.Room_id, Room.Room_type
FROM Room
LEFT JOIN Booking ON Room.Room_id = Booking.Room_id
WHERE Booking.Room_id IS NULL;
```

---

### 🔹 Step 5: I Drew an ER Diagram

This is the map that shows how all the tables are connected together:
![ER Diagram](https://github.com/AuntBawHein/Hotel_Reservation_Management_System_SQL/assets/150255399/21d27e9f-bb00-47d7-9a86-b9a36a8b6a93)

Conclusion

I built a hotel reservation system using SQL and connected all the important parts like Customer, Booking, Room, and Payment. When I looked at my ER diagram, I saw that the Booking table is the most connected because it links with more tables than any other one. I noticed that the Room table is shared by both Booking and Facility, but the Facility table is only connected to Room, which means it is less important in the system. This helped me understand that Booking is the main center of the system, while tables like Review and Feedback are more like extra parts that give more details but aren’t connected to many others.


---

### 🔹 Step 6: I Wrote a Report

I also created a document to explain my project:
📄 [Download My Project DOCX](https://github.com/AuntBawHein/Hotel_Reservation_Management_System_SQL/files/14392013/hotel_reservation_system_words_project_sql.docx)

---

## 6. 🎓 What I Learned

Here’s what I learned from this project:

- How to make a **real database system** using SQL
- How to connect tables using **foreign keys**
- How to write SQL **queries** to get answers
- How to draw an **ER diagram**
- How real businesses like hotels **store information**

---
