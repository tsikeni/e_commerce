"# e_commerce" 

**##Technologies Used
**
Java 11
Spring Boot
Spring Data JPA (Hibernate)
MySQL
Maven
Lombok
JavaMailSender for email functionality

**##Project Features
**
Order Management: Users can place orders for physical and digital products.
Gift Cards: Sent to users on their birthdays via email & Automatically generated when a user purchases 10 or more products in a single day.
User Management: Includes user-specific order tracking and email notifications.
Email Notifications: Gift cards and order confirmations are sent via email using Spring Boot's JavaMailSender.
RESTful API: Endpoints are provided for order processing and gift card management.


**##System Design
**The system follows a 3-tier architecture with distinct layers for controllers, services, and repositories, adhering to object-oriented principles.

**##Setup Instructions
**
Java Development Kit (JDK) (Version 11 or later)
Maven (For dependency management and building the project)
MySQL (Version 8.0 or later)
IDE (IntelliJ, Eclipse, or any preferred Java IDE)


**Step-by-Step Setup
**
1. Clone the repository:
2. Configure the MySQL Database
3. Run Maven to Install Dependencies
4. Run the Application
5. Access the Application: at http://localhost:8081.



**API Documentation
**


**1. Users
**##Create a New User:
POST /api/users


{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123",
  "birthday": "1990-10-14"
}
Description: This endpoint allows you to create a new user by providing their name, email, password, and birthday/date of birth.

**2. Orders 
**##Place an order
POST /api/orders?userId=1

{
  "items": [
    {
      "type": "physical",
      "productName": "Laptop",
      "price": 1200,
      "quantity": 1,
      "shippingWeight": 2.5
    },
    {
      "type": "digital",
      "productName": "E-book",
      "price": 30,
      "quantity": 1
    }
  ],
  "paymentMethod": "CreditCard"
}

Description: This endpoint allows a user (specified by the userId query parameter) to place an order with various products, including physical and digital items.

**3.Gift Cards
**
##Send a Gift Card:
POST /api/giftcards/send


[
  { "key": "senderEmail", "value": "john@example.com", "type": "text" },
  { "key": "receiverEmail", "value": "tsikeniiratuzi@gmail.com", "type": "text" },
  { "key": "amount", "value": "50.0", "type": "text" }
]

Description: This endpoint allows a user to send a gift card to another user by specifying the sender's and receiver's email addresses and the gift card amount.



**##Here are quick summaries of the changes made and why:
**
Created user class/clients 
allowed order to be placed basing on specific userId 
users can send each other giftcards and giftcards can be redeemed 
CreateOrderRequest Class: Added payment method field for handling different payment options.
Payment Class: Added order association and status tracking for payments.
BirthdayGiftCardService: Scheduled birthday gift card sending feature.
EmailService: Centralized email logic to send gift cards and notifications.


