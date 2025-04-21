# Hotel Reservation Management System Using SQL  
---

## 1. Introduction

Hi! My name is Aunt Baw Hein, but you can also call me Zi Wei. I created a fun school project called the **Hotel Reservation Management System**. I built this using a language called **SQL**, which is used to communicate with databases and manage information like bookings, customers, and payments.

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



## Step 2: I Created and Inserted Tables Using SQL

### Clerk Table

```sql
CREATE TABLE Clerk(
    Clerk_id INT PRIMARY KEY,  -- I assigned a unique ID to each clerk
    Clerk_firstname VARCHAR(100),  -- I stored the clerk's first name
    Clerk_lastname VARCHAR(100),  -- I stored the clerk's last name
    Clerk_age INT,  -- I recorded their age
    Clerk_gender VARCHAR(100),  -- I noted their gender
    Clerk_email VARCHAR(100),  -- I saved their email address
    Clerk_position VARCHAR(100),  -- I mentioned their job position
    Clerk_salary DECIMAL(10,2),  -- I included their salary
    Clerk_address VARCHAR(100),  -- I added their home address
    Clerk_contact_num VARCHAR(100)  -- I stored their contact number
);
```

![image](https://github.com/user-attachments/assets/af2e45c7-8ec3-4624-83c7-41847e75a0bf)

### Conclusion 

The output that I got is a full list of 10 clerks showing their names, ages, emails, job positions, salaries, and contact details. I noticed that the clerk with the highest salary is David Taylor, who works as a Hospital Administrator earning 75,000, while the lowest salary is 48,000 shared by Emma Johnson and Daniel Anderson. When I compared the genders, I saw that there are more male clerks (5) than female clerks (5), showing an equal balance. I also realized that different job positions like Pharmacist and IT Support Specialist have similar salaries (60,000), while higher roles like Hospital Administrator earn more, which helps me understand how roles affect salary.

### Customer Table

```sql
CREATE TABLE Customer(
    Cus_id INT PRIMARY KEY,  -- I assigned a unique ID to each customer
    Cus_firstname VARCHAR(100),  -- I stored the customer's first name
    Cus_lastname VARCHAR(100),  -- I stored the customer's last name
    Cus_age INT,  -- I recorded their age
    Cus_gender VARCHAR(100),  -- I noted their gender
    Cus_nationality VARCHAR(100),  -- I included their nationality
    Cus_email VARCHAR(100),  -- I saved their email address
    Cus_address VARCHAR(100),  -- I added their home address
    Cus_phone_number VARCHAR(100),  -- I stored their phone number
    Cus_password_number VARCHAR(100)  -- I assigned a password for their account
);
```

![image](https://github.com/user-attachments/assets/b77c3d7f-92b0-49cd-8c14-b96192c66c44)

### Conclusion

The output that I got is a list of 10 customers with their personal details like name, age, gender, nationality, and contact information. I noticed that **more male customers (5) are from Canada and Australia**, while **most female customers (3 out of 5) are from the USA and UK**. When I compared the ages, I saw that **the oldest person is 45 years old** and **the youngest is 25**, which shows that the hotel serves both younger and older people. This helped me understand how I can use SQL to **compare data, find patterns, and make useful observations** just by running a simple query.

### Room Table

```sql
CREATE TABLE Room(
    Room_id INT PRIMARY KEY,  -- I assigned a unique ID to each room
    Room_type VARCHAR(100),  -- I specified the type of room
    Room_price_per_night DECIMAL(10,2),  -- I set the price per night
    Room_max_number INT,  -- I defined the maximum occupancy
    Room_description TEXT,  -- I described the room
    Room_amenities VARCHAR(255),  -- I listed the amenities
    Room_status VARCHAR(50),  -- I indicated if the room is available or occupied
    Room_last_cleaned DATE  -- I noted the last cleaning date
);
```

![image](https://github.com/user-attachments/assets/ae7e7380-4180-461d-b59f-18a32f4d4d11)

**Conclusions**

The output that I got is a list of 10 different room types in the hotel, including their price, how many people can stay, what they include, and when they were last cleaned. I saw that the most expensive room is the **Presidential Suite** at **500.00**, and the cheapest one is the **Economy Room** at **60.00**, which means the price difference is quite big depending on luxury. I noticed that some rooms like the **Deluxe Single** and **Executive Suite** are already occupied, while the rest are available. I also compared the amenities and found that more expensive rooms usually include extra features like **Jacuzzi and Mini Bar**, while cheaper rooms have basic things like **WiFi and TV** only.

### Booking Table

```sql
CREATE TABLE Booking(
    Bk_id INT PRIMARY KEY,  -- I assigned a unique ID to each booking
    Bk_date DATE,  -- I recorded the booking date
    Bk_check_in DATE,  -- I noted the check-in date
    Bk_check_out DATE,  -- I noted the check-out date
    Bk_breakfast VARCHAR(100),  -- I specified if breakfast is included
    Bk_dinner VARCHAR(100),  -- I specified if dinner is included
    Clerk_id INT,  -- I linked the booking to a clerk
    Cus_id INT,  -- I linked the booking to a customer
    Room_id INT,  -- I linked the booking to a room
    Booking_status VARCHAR(50),  -- I indicated the booking status
    Booking_total_cost DECIMAL(10,2),  -- I calculated the total cost
    FOREIGN KEY (Clerk_id) REFERENCES Clerk(Clerk_id),
    FOREIGN KEY (Cus_id) REFERENCES Customer(Cus_id),
    FOREIGN KEY (Room_id) REFERENCES Room(Room_id)
);
```

![image](https://github.com/user-attachments/assets/4aaf0e73-0284-4827-8f11-479f679846dc)

**Conclusions**

The output that I got is a table showing 10 bookings with check-in and check-out dates, meals included, total cost, and whether the booking is confirmed or still pending. I noticed that the **highest booking cost** is **900.00**, while the **lowest** is **500.00**, which tells me that customers pay different amounts depending on their room and meal options. I also saw that **Confirmed bookings** are more common (6 out of 10), showing that more customers went ahead with their reservation than those who are still waiting. When comparing meals, some bookings had **both breakfast and dinner**, while others had **none**, showing that not all guests choose meal packages during their stay.

### Guest Table

```sql
CREATE TABLE Guest(
    Guest_id INT PRIMARY KEY,  -- I assigned a unique ID to each guest
    Guest_firstname VARCHAR(100),  -- I stored the guest's first name
    Guest_lastname VARCHAR(100),  -- I stored the guest's last name
    Guest_age INT,  -- I recorded their age
    Guest_gender VARCHAR(50),  -- I noted their gender
    Guest_email VARCHAR(100),  -- I saved their email address
    Guest_contact_num VARCHAR(255),  -- I stored their contact number
    Guest_nationality VARCHAR(100),  -- I included their nationality
    Guest_special_requests VARCHAR(255),  -- I noted any special requests
    Booking_id INT,  -- I linked the guest to a booking
    FOREIGN KEY (Booking_id) REFERENCES Booking(Bk_id)
);
```

![image](https://github.com/user-attachments/assets/4af97769-3e9e-4c3b-bcbb-657581bd8fd1)

**Conclusions**

The output that I got is a list of 10 hotel guests with their names, ages, nationalities, and any special requests they made when booking. I noticed that **more male guests (5)** requested things like vegetarian meals or early check-out, while **female guests (5)** asked for things like extra towels or a quiet room. When I compared the ages, **the oldest guest was 36** and **the youngest was 26**, which shows that the hotel serves adults of all ages. I also saw that **USA and Canada had the most guests**, which helped me understand where most visitors are from and what kinds of requests are more popular depending on gender or nationality.

### Payment Table

```sql
CREATE TABLE Payment(
    Pymt_id INT PRIMARY KEY,  -- I assigned a unique ID to each payment
    Pymt_amount DECIMAL(10,2),  -- I recorded the payment amount
    Pymt_date DATE,  -- I noted the payment date
    Payment_method VARCHAR(50),  -- I specified the payment method
    Payment_status VARCHAR(50),  -- I indicated the payment status
    Booking_id INT,  -- I linked the payment to a booking
    FOREIGN KEY (Booking_id) REFERENCES Booking(Bk_id)
);
```

![image](https://github.com/user-attachments/assets/d06660ef-8e5e-41d0-b352-4872236581c3)

**Conclusions**

The output that I got is a list of 10 payments made by hotel customers, including how much they paid, when they paid, what method they used (like credit card or PayPal), and whether the payment was successful or not. I noticed that **more payments were successful (6)** compared to those that are still **pending (4)**. When I compared payment methods, **credit card was used the most (4 times)**, while **PayPal and debit card were each used 3 times**. I also saw that the **highest payment made was 300.00** and the **lowest was 150.00**, so I learned how to spot trends and compare results just by looking at payment amounts and statuses.

### Facility Table

```sql
CREATE TABLE Facility(
    Facility_id INT PRIMARY KEY,  -- I assigned a unique ID to each facility
    Facility_name VARCHAR(100),  -- I named the facility
    Facility_description VARCHAR(255),  -- I described the facility
    Facility_capacity INT,  -- I defined the capacity
    Facility_location VARCHAR(255),  -- I specified the location
    Room_id INT,  -- I linked the facility to a room
    FOREIGN KEY (Room_id) REFERENCES Room(Room_id)
);
```

![image](https://github.com/user-attachments/assets/8f2ac3ae-425b-476d-a97e-18b2054e2812)

### Conclusion

The output that I got is a list of different facilities in a building, showing their names, descriptions, how many people each can hold, where they are located, and their room numbers. I noticed that the **Banquet Hall** has the highest capacity of **100 people**, while the **Spa & Wellness Center** can only hold **10 people**, which is the smallest. This means the Banquet Hall is **10 times bigger** in capacity than the Spa. I also saw that **two facilities** are on the **Ground Floor** (Fitness Center and Banquet Hall), and **two are on Floor 2** (Conference Room A and Game Room), so I can compare locations as well.

### Review Table

```sql
CREATE TABLE Review(
    Review_id INT PRIMARY KEY,  -- I assigned a unique ID to each review
    Review_rating INT,  -- I recorded the rating
    Review_comment VARCHAR(255),  -- I included the review comment
    Booking_id INT,  -- I linked the review to a booking
    FOREIGN KEY (Booking_id) REFERENCES Booking(Bk_id)
);
```
![image](https://github.com/user-attachments/assets/26935f50-9a29-48a5-baf3-85b3c76eb9c0)

### Conclusion

The output that I got is a list of reviews made by customers, each one linked to a real booking. I can see that the review ratings range from **3 to 5**, which shows a mix of average and excellent experiences. For example, **Review ID 23** gave the highest rating of **5**, saying the stay was “exceptional,” while **Review ID 22 and 27** gave lower ratings of **3**, mentioning things that could be better. I notice that **most reviews are rated 4**, which means many people were happy, but not totally amazed.

### Feedback Table

```sql
CREATE TABLE Feedback(
    Feedback_id INT PRIMARY KEY,  -- I assigned a unique ID to each feedback
    Feedback_comment VARCHAR(255),  -- I included the feedback comment
    Cus_id INT,  -- I linked the feedback to a customer
    FOREIGN KEY (Cus_id) REFERENCES Customer(Cus_id)
);
```

![image](https://github.com/user-attachments/assets/0edf67e2-014a-43dd-a8a3-4f021db0a24c)

### Conclusion 

The output that I got is a list of **feedback comments from 10 customers**, each connected to a customer ID. I noticed that **most feedback is positive**, with words like "excellent," "clean," "helpful," and "impressed" appearing several times — showing that people were happy with their experience. I found that only **1 out of 10 feedback comments (Customer ID 6)** mentioned a **minor issue**, which means **90% of the feedback was completely positive**. I can say that **I saw more compliments than complaints**, so overall, the service seems to have made customers feel satisfied and supported.

---

### Step 3: I Added Sample Data

Then I added information to test it.

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

## Step 4: 10 Real Questions and Answers with SQL Code (Humanized)

---

### Q1: **How did you know who booked a room and whether they paid or not?**  
**I** used SQL `JOINs` to connect the **Customer**, **Room**, and **Payment** tables. This helped me see not just who booked what room, but also if they paid for it. The `LEFT JOIN` was really helpful to still show unpaid bookings.

```sql
SELECT Customer.Cus_firstname, Room.Room_type, Payment.Payment_status
FROM Booking
JOIN Customer ON Booking.Cus_id = Customer.Cus_id
JOIN Room ON Booking.Room_id = Room.Room_id
LEFT JOIN Payment ON Booking.Bk_id = Payment.Booking_id;
```

---

### Q2: **How did you find only the customers who completed their payment?**  
**I** filtered out only the bookings where the payment status says `'Successful'`. This way, I was only showing customers who actually paid.

```sql
SELECT Customer.Cus_firstname, Room.Room_type, Payment.Payment_status
FROM Booking
JOIN Customer ON Booking.Cus_id = Customer.Cus_id
JOIN Room ON Booking.Room_id = Room.Room_id
JOIN Payment ON Booking.Bk_id = Payment.Booking_id
WHERE Payment.Payment_status = 'Successful';
```

---

### Q3: **Can you show which guests stayed in which room?**  
Yes! **I** linked the **Room**, **Booking**, and **Guest** tables so I could track down exactly which guest stayed in which room. This makes it easier for staff to personalize their service.

```sql
SELECT Room.Room_type, Guest.Guest_firstname
FROM Room
JOIN Booking ON Room.Room_id = Booking.Room_id
JOIN Guest ON Booking.Bk_id = Guest.Booking_id;
```

---

### Q4: **How did you find out how many bookings each customer made?**  
**I** grouped the bookings by customer and used `COUNT()` to see how often each person booked. This helped me find loyal or repeat customers.

```sql
SELECT Customer.Cus_firstname, COUNT(Booking.Bk_id) AS Total_Bookings
FROM Customer
LEFT JOIN Booking ON Customer.Cus_id = Booking.Cus_id
GROUP BY Customer.Cus_firstname;
```

---

### Q5: **Did you check which rooms were never booked at all?**  
Yes, I did! **I** used a `LEFT JOIN` and filtered out rooms that **don’t appear in the Booking table**. These are rooms that were never used.

```sql
SELECT Room.Room_id, Room.Room_type
FROM Room
LEFT JOIN Booking ON Room.Room_id = Booking.Room_id
WHERE Booking.Room_id IS NULL;
```

---

### Q6: **How did you know which clerk handled each booking?**  
**I** joined the **Booking** and **Clerk** tables so I could match clerks with the bookings they helped with. This is useful for tracking staff performance or assigning responsibility.

```sql
SELECT Clerk.Clerk_firstname, Customer.Cus_firstname
FROM Booking
JOIN Clerk ON Booking.Clerk_id = Clerk.Clerk_id
JOIN Customer ON Booking.Cus_id = Customer.Cus_id;
```

---

### Q7: **How do you show which facilities are available in each room?**  
**I** connected the **Facility** and **Room** tables. This helped me list all the amenities guests can use depending on their room type, like spa, gym, or rooftop.

```sql
SELECT Room.Room_type, Facility.Facility_name
FROM Facility
JOIN Room ON Facility.Room_id = Room.Room_id;
```

---

### Q8: **How do you see the ratings and comments from guests?**  
**I** just used a simple `SELECT` query from the **Review** table to view all the guest reviews and their ratings. It helped me get an idea of what guests liked or didn’t like.

```sql
SELECT Review.Review_comment, Review.Review_rating
FROM Review;
```

---

### Q9: **How did you get feedback from customers and link it to their names?**  
**I** joined the **Feedback** table with the **Customer** table so I could see who said what. It was cool to match comments with actual customers.

```sql
SELECT Customer.Cus_firstname, Feedback.Feedback_comment
FROM Feedback
JOIN Customer ON Feedback.Cus_id = Customer.Cus_id;
```

---

### Q10: **Can you find guests who had special requests?**  
Yes. **I** just searched the **Guest** table and looked for any rows where the `Guest_special_requests` field wasn't empty.

```sql
SELECT Guest_firstname, Guest_special_requests
FROM Guest
WHERE Guest_special_requests IS NOT NULL;
```

---

**Q11: What was one challenge you faced while working on this project?**  
**I** struggled a little when I saw that some reviews didn’t have a booking ID, and that caused an error when I tried to re-insert new reviews. I fixed it by deleting the old ones with no booking, but it helped me learn why every review needs to connect to a real booking. I also realized how important it is to check for duplicates before inserting data. This experience taught me that **even small mistakes in a database can break a lot of things**.
---

---

### Step 5: I Drew an ER Diagram

This is the map that shows how all the tables are connected together:

![ER Diagram](https://github.com/AuntBawHein/Hotel_Reservation_Management_System_SQL/assets/150255399/21d27e9f-bb00-47d7-9a86-b9a36a8b6a93)

### Conclusion

I built a hotel reservation system using SQL and connected all the important parts like Customer, Booking, Room, and Payment. When I looked at my ER diagram, I saw that the Booking table is the most connected because it links with more tables than any other one. I noticed that the Room table is shared by both Booking and Facility, but the Facility table is only connected to Room, which means it is less important in the system. This helped me understand that Booking is the main center of the system, while tables like Review and Feedback are more like extra parts that give more details but aren’t connected to many others.


---

### Step 6: I Wrote a Report

I also created a document to explain my project:

[Hospital_management_system_project_words_sql.docx](https://github.com/user-attachments/files/19833239/Hospital_management_system_project_words_sql.docx)

(https://github.com/AuntBawHein/Hotel_Reservation_Management_System_SQL/files/14392013/hotel_reservation_system_words_project_sql.docx)

---

## 6. What I Learned

Here’s what I learned from this project:

- How to make a **real database system** using SQL
- How to connect tables using **foreign keys**
- How to write SQL **queries** to get answers
- How to draw an **ER diagram**
- How real businesses like hotels **store information**

---
