# Hotel_Reservation_Management_System_SQL

The scope of this project is to design a Hotel Reservation System. 
Problem statement/ Idea 
 1. Think how we're going to create lots of objects first, before adding more attributes. 
 2. Think and create about entities or attributes inside lots of objects. 
 3. Design and create ER diagram. 
 4. Finally, run each table to make sure that ER diagram are in one place. 

Below are the processes and questions that I'm going to create step by step based on this project here.

-- Step 1: I'm going to create 10 objects for Hotel Reservation System. 
-- These are all our objects. 

-- 1. Clerk 
-- 2. Customer 
-- 3. Room
-- 4. Booking 
-- 5. Guest
-- 6. Payment 
-- 7. Facility 
-- 8. Payment 
-- 9. Review 
-- 10. Feedback


-- Step 2: Let's create our table here one by one. 

-- Creating Clerk table here.
CREATE TABLE Clerk(
    Clerk_id INT PRIMARY KEY, 
    Clerk_firstname VARCHAR(100), 
    Clerk_lastname VARCHAR(100), 
    Clerk_age INT, 
    Clerk_gender VARCHAR(100), 
    Clerk_email VARCHAR(100), 
    Clerk_position VARCHAR(100), 
    Clerk_salary DECIMAL(10,2), 
    Clerk_address VARCHAR(100), 
    Clerk_contact_num VARCHAR(100)
);



-- Creating Customer table here.
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




-- Creating Room table here.
CREATE TABLE Room(
    Room_id INT PRIMARY KEY, 
    Room_type VARCHAR(100),
    Room_price_per_night DECIMAL(10,2), 
    Room_max_number INT,
    Room_description TEXT,
    Room_amenities VARCHAR(255),
    Room_status VARCHAR(50),
    Room_last_cleaned DATE
);






-- Creating Booking table here.
CREATE TABLE Booking(
    Bk_id INT PRIMARY KEY, 
    Bk_date DATE, 
    Bk_check_in DATE,
    Bk_check_out DATE, 
    Bk_breakfast VARCHAR(100), 
    Bk_dinner VARCHAR(100),
    Clerk_id INT, 
    Cus_id INT, 
    Room_id INT, 
    Booking_status VARCHAR(50),
    Booking_total_cost DECIMAL(10,2),
    FOREIGN KEY (Clerk_id) REFERENCES Clerk(Clerk_id), 
    FOREIGN KEY (Cus_id) REFERENCES Customer(Cus_id), 
    FOREIGN KEY (Room_id) REFERENCES Room(Room_id)
);
-- Creating Guest table here.
CREATE TABLE Guest(
    Guest_id INT PRIMARY KEY, 
    Guest_firstname VARCHAR(100), 
    Guest_lastname VARCHAR(100), 
    Guest_age INT,
    Guest_gender VARCHAR(50),
    Guest_email VARCHAR(100),
    Guest_contact_num VARCHAR(255),
    Guest_nationality VARCHAR(100),
    Guest_special_requests VARCHAR(255),
    Booking_id INT, 
    FOREIGN KEY (Booking_id) REFERENCES Booking(Bk_id)
);



-- Creating Payment table here.
CREATE TABLE Payment(
    Pymt_id INT PRIMARY KEY, 
    Pymt_amount DECIMAL(10,2), 
    Pymt_date DATE, 
    Payment_method VARCHAR(50),
    Payment_status VARCHAR(50),
    Booking_id INT, 
    FOREIGN KEY (Booking_id) REFERENCES Booking(Bk_id)
);







-- Creating Facility table here.
CREATE TABLE Facility(
    Facility_id INT PRIMARY KEY, 
    Facility_name VARCHAR(100), 
    Facility_description VARCHAR(255),
    Facility_capacity INT,
    Facility_location VARCHAR(255),
    Room_id INT, 
    FOREIGN KEY (Room_id) REFERENCES Room(Room_id)
);







-- Creating Review table here. 
CREATE TABLE Review(
    Review_id INT PRIMARY KEY, 
    Review_rating INT, 
    Review_comment VARCHAR(255), 
    Booking_id INT, 
    FOREIGN KEY (Booking_id) REFERENCES Booking(Bk_id)
);

-- Creating Feedback table here. 
CREATE TABLE Feedback(
    Feedback_id INT PRIMARY KEY, 
    Feedback_comment VARCHAR(255), 
    Cus_id INT, 
    FOREIGN KEY (Cus_id) REFERENCES Customer(Cus_id) 
);


-- Step 3: We're going to insert some data in each table here. 
-- Inserting data into Clerk table.
INSERT INTO Clerk (Clerk_id, Clerk_firstname, Clerk_lastname, Clerk_age, Clerk_gender, Clerk_email, Clerk_position, Clerk_salary, 
Clerk_address, Clerk_contact_num) VALUES 
(3, 'Michael', 'Jordan', 35, 'Male', 'michael.jordan@email.com', 'Front Desk Manager', 55000.00, '789 Maple Avenue', '456-789-0123'),
(4, 'Emma', 'Johnson', 32, 'Female', 'emma.johnson@email.com', 'Medical Records Clerk', 48000.00, '567 Pine Street', '789-012-3456'),
(5, 'Robert', 'Williams', 40, 'Male', 'robert.williams@email.com', 'Pharmacist', 60000.00, '678 Oak Lane', '012-345-6789'),
(6, 'Sophia', 'Miller', 28, 'Female', 'sophia.miller@email.com', 'Laboratory Technician', 50000.00, '890 Cedar Road', '345-678-9012'),
(7, 'David', 'Taylor', 45, 'Male', 'david.taylor@email.com', 'Hospital Administrator', 75000.00, '901 Elm Street', '678-901-2345'),
(8, 'Olivia', 'Brown', 30, 'Female', 'olivia.brown@email.com', 'Radiologist', 70000.00, '123 Birch Avenue', '901-234-5678'),
(9, 'Daniel', 'Anderson', 35, 'Male', 'daniel.anderson@email.com', 'Emergency Room Nurse', 48000.00, '234 Pine Lane', '234-567-8901'),
(10, 'Sophie', 'Turner', 32, 'Female', 'sophie.turner@email.com', 'Pharmacy Technician', 52000.00, '345 Cedar Road', '567-890-1234'),
(11, 'William', 'Clark', 38, 'Male', 'william.clark@email.com', 'IT Support Specialist', 60000.00, '456 Oak Lane', '789-012-3456'),
(12, 'Grace', 'Evans', 31, 'Female', 'grace.evans@email.com', 'X-ray Technician', 55000.00, '567 Pine Street', '012-345-6789');
-- Newid function generates any random information here.
SELECT * FROM Clerk
ORDER BY NEWID();  


-- Inserting data into Customer table
INSERT INTO Customer(Cus_id, Cus_firstname, Cus_lastname, Cus_age, Cus_gender, Cus_nationality, Cus_email, Cus_address, Cus_phone_number
, Cus_password_number) VALUES 
(1, 'Emma', 'Johnson', 28, 'Female', 'USA', 'emma.johnson@email.com', '123 Main Street', '123-456-7890', 'password123'),
(2, 'Michael', 'Smith', 35, 'Male', 'Canada', 'michael.smith@email.com', '456 Oak Avenue', '987-654-3210', 'pass456word'),
(3, 'Sophie', 'Turner', 25, 'Female', 'UK', 'sophie.turner@email.com', '789 Pine Lane', '234-567-8901', 'secure789'),
(4, 'Daniel', 'Anderson', 32, 'Male', 'Australia', 'daniel.anderson@email.com', '890 Cedar Road', '345-678-9012', 'password432'),
(5, 'Olivia', 'Brown', 30, 'Female', 'USA', 'olivia.brown@email.com', '901 Elm Street', '567-890-1234', 'pass567word'),
(6, 'William', 'Clark', 38, 'Male', 'Canada', 'william.clark@email.com', '123 Birch Avenue', '678-901-2345', 'secure678'),
(7, 'Grace', 'Evans', 31, 'Female', 'UK', 'grace.evans@email.com', '234 Pine Lane', '789-012-3456', 'password789'),
(8, 'David', 'Taylor', 45, 'Male', 'Australia', 'david.taylor@email.com', '345 Cedar Road', '901-234-5678', 'pass901word'),
(9, 'Sophia', 'Miller', 28, 'Female', 'USA', 'sophia.miller@email.com', '456 Oak Lane', '012-345-6789', 'secure012'),
(10, 'Robert', 'Williams', 40, 'Male', 'Canada', 'robert.williams@email.com', '567 Pine Street', '234-567-8901', 'password234'); 
-- Newid function generates any random information here.
SELECT * FROM Customer
ORDER BY NEWID();  

-- Inserting data into Room table
INSERT INTO Room(Room_id, Room_type, Room_price_per_night, Room_max_number, Room_description, Room_amenities, Room_status, 
Room_last_cleaned) VALUES
(101, 'Standard Single', 80.00, 1, 'Cozy single room with a comfortable bed', 'WiFi, TV, Air Conditioning', 'Available', '2023-01-15'),
(102, 'Standard Double', 120.00, 2, 'Spacious double room with twin beds', 'WiFi, TV, Air Conditioning', 'Available', '2023-01-18'),
(103, 'Deluxe Single', 100.00, 1, 'Luxurious single room with additional amenities', 'WiFi, TV, Air Conditioning, Mini Bar', 'Occupied', '2023-01-12'),
(104, 'Deluxe Double', 150.00, 2, 'Elegant double room with a king-size bed', 'WiFi, TV, Air Conditioning, Mini Bar', 'Available', 
'2023-01-20'),
(105, 'Suite', 200.00, 2, 'Exclusive suite with a separate living area', 'WiFi, TV, Air Conditioning, Mini Bar, Jacuzzi', 'Available', 
'2023-01-22'),
(106, 'Family Room', 180.00, 4, 'Spacious room suitable for a family', 'WiFi, TV, Air Conditioning', 'Available', '2023-01-17'),
(107, 'Executive Suite', 250.00, 2, 'Luxurious suite with a panoramic view', 'WiFi, TV, Air Conditioning, Mini Bar, Jacuzzi', 'Occupied'
, '2023-01-14'),
(108, 'Standard Twin', 110.00, 2, 'Comfortable room with twin beds', 'WiFi, TV, Air Conditioning', 'Available', '2023-01-16'),
(109, 'Presidential Suite', 500.00, 4, 'The epitome of luxury and sophistication', 'WiFi, TV, Air Conditioning, Mini Bar, Jacuzzi, 
Private Pool', 'Available', '2023-01-25'),
(110, 'Economy Room', 60.00, 1, 'Budget-friendly room with essential amenities', 'WiFi, TV', 'Available', '2023-01-10');
-- Newid function generates any random information here.
SELECT * FROM Room
ORDER BY NEWID();  

-- Inserting data into Booking table
INSERT INTO Booking(Bk_id, Bk_date, Bk_check_in, Bk_check_out, Bk_breakfast, Bk_dinner, Clerk_id, Cus_id, Room_id, Booking_status, Booking_total_cost)
VALUES 
(3, '2024-02-10', '2024-02-15', '2024-02-20', 'Included', 'Not Included', 3, 1, 101, 'Confirmed', 500.00),
(4, '2024-02-12', '2024-02-18', '2024-02-22', 'Not Included', 'Included', 4, 2, 102, 'Pending', 600.00),
(5, '2024-02-14', '2024-02-20', '2024-02-25', 'Included', 'Included', 5, 3, 103, 'Confirmed', 700.00),
(6, '2024-02-16', '2024-02-25', '2024-02-28', 'Not Included', 'Included', 6, 4, 104, 'Confirmed', 550.00),
(7, '2024-02-18', '2024-02-22', '2024-02-27', 'Included', 'Not Included', 7, 5, 105, 'Pending', 800.00),
(8, '2024-02-20', '2024-02-28', '2024-03-05', 'Not Included', 'Not Included', 8, 6, 106, 'Confirmed', 900.00),
(9, '2024-02-22', '2024-03-01', '2024-03-06', 'Included', 'Included', 9, 7, 107, 'Pending', 750.00),
(10, '2024-02-24', '2024-03-05', '2024-03-10', 'Included', 'Not Included', 10, 8, 108, 'Confirmed', 650.00),
(11, '2024-02-26', '2024-03-08', '2024-03-13', 'Not Included', 'Included', 11, 9, 109, 'Confirmed', 700.00),
(12, '2024-02-28', '2024-03-10', '2024-03-15', 'Included', 'Included', 12, 10, 110, 'Pending', 850.00);
-- Newid function generates any random information here.
SELECT * FROM Booking ORDER BY NEWID();  


-- Inserting data into Guest table
INSERT INTO Guest (Guest_id, Guest_firstname, Guest_lastname, Guest_age, Guest_gender, Guest_email, Guest_contact_num, 
                   Guest_nationality, Guest_special_requests, Booking_id)
VALUES 
(11, 'Elijah', 'Adams', 29, 'Male', 'elijah.adams@email.com', '345-678-9012', 'USA', 'Late Check-in', 3),
(12, 'Ava', 'Baker', 26, 'Female', 'ava.baker@email.com', '456-789-0123', 'Canada', 'Quiet Room', 5),
(13, 'Liam', 'Carter', 31, 'Male', 'liam.carter@email.com', '567-890-1234', 'UK', 'Vegetarian Meals', 6),
(14, 'Mia', 'Davis', 27, 'Female', 'mia.davis@email.com', '678-901-2345', 'Australia', 'Airport Pickup', 7),
(15, 'Noah', 'Edwards', 33, 'Male', 'noah.edwards@email.com', '789-012-3456', 'USA', 'Early Check-out', 8),
(16, 'Emma', 'Fisher', 29, 'Female', 'emma.fisher@email.com', '890-123-4567', 'Canada', 'Extra Towels', 4),
(17, 'Jackson', 'Gibson', 36, 'Male', 'jackson.gibson@email.com', '901-234-5678', 'UK', 'Room with a View', 11),
(18, 'Olivia', 'Harrison', 32, 'Female', 'olivia.harrison@email.com', '012-345-6789', 'Australia', 'Special Occasion', 12),
(19, 'Ethan', 'Irwin', 30, 'Male', 'ethan.irwin@email.com', '123-456-7890', 'USA', 'Late Check-in', 10),
(20, 'Isabella', 'Jenkins', 28, 'Female', 'isabella.jenkins@email.com', '234-567-8901', 'Canada', 'High-floor Room', 9);
-- Newid function generates any random information here.
SELECT * FROM Guest
ORDER BY NEWID();  

-- Inserting data into Payment table
INSERT INTO Payment (Pymt_id, Pymt_amount, Pymt_date, Payment_method, Payment_status, Booking_id)
VALUES 
(21, 150.00, '2024-02-20', 'Credit Card', 'Successful', 11),
(22, 200.00, '2024-02-22', 'PayPal', 'Successful', 12),
(23, 250.00, '2024-02-25', 'Credit Card', 'Pending', 3),
(24, 180.00, '2024-02-28', 'Debit Card', 'Successful', 4),
(25, 300.00, '2024-02-27', 'PayPal', 'Pending', 5),
(26, 220.00, '2024-03-05', 'Credit Card', 'Successful', 6),
(27, 190.00, '2024-03-06', 'Debit Card', 'Pending', 7),
(28, 280.00, '2024-03-10', 'Credit Card', 'Successful', 8),
(29, 240.00, '2024-03-13', 'PayPal', 'Successful', 9),
(30, 200.00, '2024-03-15', 'Debit Card', 'Pending', 10);
-- Newid function generates any random information here.
SELECT * FROM Payment
ORDER BY NEWID();  

-- Inserting data into Facility table
INSERT INTO Facility (Facility_id, Facility_name, Facility_description, Facility_capacity, Facility_location, Room_id)
VALUES 
(11, 'Conference Room A', 'Spacious conference room with modern amenities', 50, 'Floor 2', 101),
(12, 'Fitness Center', 'Fully equipped fitness center with state-of-the-art equipment', 30, 'Ground Floor', 102),
(13, 'Poolside Lounge', 'Relaxing lounge area by the pool', 20, 'Pool Area', 103),
(14, 'Business Center', 'Business-friendly space with workstations and high-speed internet', 25, 'Floor 3', 104),
(15, 'Rooftop Terrace', 'Scenic rooftop terrace with panoramic views', 40, 'Rooftop', 105),
(16, 'Kids Playroom', 'Playroom for children with various games and activities', 15, 'Floor 1', 106),
(17, 'Spa & Wellness Center', 'Wellness center offering spa treatments and relaxation', 10, 'Floor 4', 107),
(18, 'Banquet Hall', 'Elegant banquet hall for special events and gatherings', 100, 'Ground Floor', 108),
(19, 'Outdoor Garden', 'Beautiful garden area for outdoor events', 30, 'Garden Area', 109),
(20, 'Game Room', 'Entertainment room with a variety of games', 20, 'Floor 2', 110);
-- Newid function  generates any random information here.
SELECT * FROM Facility
ORDER BY NEWID();  


-- Inserting data into Review table
INSERT INTO Review (Review_id, Review_rating, Review_comment)
VALUES 
(11, 4.5, 'Great experience! The staff was very friendly and the room was clean and comfortable.'),
(12, 3.8, 'Good service, but the breakfast options could be improved.'),
(13, 5.0, 'Exceptional stay! The facilities were top-notch, and the location was perfect.'),
(14, 4.0, 'Comfortable beds and a fantastic view from the room.'),
(15, 4.2, 'Friendly staff, but the Wi-Fi signal was a bit weak in the room.'),
(16, 4.7, 'Beautifully decorated rooms with modern amenities.'),
(17, 3.5, 'Average experience. Some noise from nearby construction.'),
(18, 4.9, 'Outstanding service and attention to detail. Will definitely come back!'),
(19, 3.0, 'The room was clean, but the air conditioning wasn’t working properly.'),
(20, 4.4, 'Lovely atmosphere and a great location. Highly recommended!');
-- Newid function generates any random information here.
SELECT * FROM Review
ORDER BY NEWID();

-- Inserting data into Feedback table
INSERT INTO Feedback (Feedback_id, Feedback_comment, Cus_id)
VALUES 
(11, 'Excellent service! The staff was very helpful and friendly.', 1),
(12, 'Clean and comfortable rooms. Great value for money.', 2),
(13, 'The facilities were well-maintained, and the location was convenient.', 3),
(14, 'Good experience overall. The staff made me feel welcome.', 4),
(15, 'Impressed with the room amenities. Will recommend to friends.', 5),
(16, 'Had a minor issue with the check-in process, but it was quickly resolved.', 6),
(17, 'The hotel exceeded my expectations. Will definitely return.', 7),
(18, 'Satisfied with the stay. The room had a nice view of the city.', 8),
(19, 'Friendly and efficient staff. Enjoyed my time at the hotel.', 9),
(20, 'Clean and quiet environment. Ideal for a relaxing stay.', 10);
-- Newid function generates any random information here. 
SELECT * FROM Feedback 
ORDER BY NEWID();

-- Step 4: We're going to make our own questions and answer using JOIN Functions.
-- Q1: Can you show me the information about all hotel bookings , like the customer's name, email, details about the room they booked 
-- and whether they have paid or not? 
SELECT Customer.Cus_firstname, Customer.Cus_lastname, Customer.Cus_email, Room.Room_type, Room.Room_description, Payment.Payment_status
FROM Booking 
JOIN Customer ON Booking.Cus_id = Customer.Cus_id 
JOIN Room ON Booking.Room_id = Room.Room_id 
LEFT JOIN Payment ON Booking.Bk_id = Payment.Booking_id;

-- Q2: What if I only want to see where customers have paid? 
SELECT Customer.Cus_firstname, Customer.Cus_lastname, Customer.Cus_email, Room.Room_type, Room.Room_description, Payment.Payment_status 
FROM Booking 
JOIN Customer ON Booking.Cus_id = Customer.Cus_id 
JOIN ROOM ON Booking.Room_id = Room.Room_id 
JOIN Payment ON Booking.Bk_id = Payment.Booking_id 
WHERE Payment.Payment_status = 'Successful'; 

-- Q3: How can I get a list of rooms with the names of guest who booked them? 
SELECT Room.Room_type, Guest.Guest_firstname, Guest.Guest_lastname 
FROM ROOM 
JOIN Booking ON Room.Room_id = Booking.Room_id
JOIN Guest ON Booking.Bk_id = Guest.Booking_id;


-- Q4: Can you tell me how many bookings each customer has made? 
SELECT Customer.Cus_id, Customer.Cus_firstname, Customer.Cus_lastname, COUNT(Booking.Bk_id) AS Total_Bookings
FROM Customer
LEFT JOIN Booking ON Customer.Cus_id = Booking.Cus_id 
GROUP BY Customer.Cus_id, Customer.Cus_firstname, Customer.Cus_lastname;

-- Q5: How can I find rooms that have never been booked before?
SELECT Room.Room_id, Room.Room_type
FROM Room
LEFT JOIN Booking ON Room.Room_id = Booking.Room_id
WHERE Booking.Room_id IS  NULL;


Step 5: I’m going to show you the table diagram of all objects and entities here.
![Hotel_reservation_entity_relationship](https://github.com/AuntBawHein/Hotel_Reservation_Management_System_SQL/assets/150255399/21d27e9f-bb00-47d7-9a86-b9a36a8b6a93)


Step 6: I’m going to show you SQL Hotel Reservation System Project database.
 [hotel_reservation_system_words_project_sql.docx](https://github.com/AuntBawHein/Hotel_Reservation_Management_System_SQL/files/14392013/hotel_reservation_system_words_project_sql.docx)


Thank you very much. 



