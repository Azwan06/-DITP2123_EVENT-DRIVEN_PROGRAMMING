# -DITP2123_EVENT-DRIVEN_PROGRAMMING

buat erd,database
inteface vending machine


QuickServe Vending Machine System (Using C#)
Programming Language & Software
Language: C#
Framework: Windows Forms (WinForms)
IDE: Visual Studio 2026 Community Edition
Database: SQL Server / MySQL
Concept: Event-Driven Programming
System Description
QuickServe Vending Machine System is a smart vending machine application developed using C# WinForms.
The system allows customers to:
Browse products
Purchase items
Make payment
Print receipt
The system allows admin to:
Manage products
Update inventory
Monitor sales
Generate reports
Products include:
Drinks
Snacks
Instant noodles
Chocolate
Stationery
Personal care items
Essential Forms (Interfaces)
1. Login Form
Functions
Admin login
Staff login
Customer guest access
C# Event Examples
C#
private void btnLogin_Click(object sender, EventArgs e)
{
    MessageBox.Show("Login Successful");
}
2. Dashboard Form
Functions
Main navigation
Sales summary
Stock alerts
Components
Panel
Buttons
Labels
Chart
3. Product Display Form
Functions
Display vending products
Product categories
Add item to cart
Controls
FlowLayoutPanel
PictureBox
Button
Label
Example Event
C#
private void btnAddToCart_Click(object sender, EventArgs e)
{
    MessageBox.Show("Product Added");
}
4. Shopping Cart Form
Functions
View selected items
Update quantity
Remove products
Calculate total price
Example Event
C#
private void numericQuantity_ValueChanged(object sender, EventArgs e)
{
    CalculateTotal();
}
5. Payment Form
Functions
Cash payment
QR payment simulation
Card payment simulation
Calculate balance
Example Event
C#
private void txtCash_TextChanged(object sender, EventArgs e)
{
    balance = cash - total;
}
6. Receipt Form
Functions
Display receipt
Print receipt
Save transaction
7. Product Management Form (Admin)
Functions
Add product
Edit product
Delete product
Upload product image
Example Event
C#
private void btnDelete_Click(object sender, EventArgs e)
{
    MessageBox.Show("Product Deleted");
}
8. Inventory Management Form
Functions
Update stock
Monitor low stock
Restock products
Example Event
C#
private void timer1_Tick(object sender, EventArgs e)
{
    CheckLowStock();
}
9. Sales Report Form
Functions
Daily sales report
Monthly sales report
Best-selling products
Controls
DataGridView
Chart
DateTimePicker
10. User Management Form
Functions
Manage admin accounts
Change password
Assign roles
Suggested Database Tables
Users
Field
Type
UserID
int
Username
varchar
Password
varchar
Role
varchar
Categories
Field
Type
CategoryID
int
CategoryName
varchar
Products
Field
Type
ProductID
int
CategoryID
int
ProductName
varchar
Price
decimal
StockQuantity
int
ProductImage
varchar
Customers
Field
Type
CustomerID
int
CustomerName
varchar
PhoneNumber
varchar
Transactions
Field
Type
TransactionID
int
CustomerID
int
TotalAmount
decimal
PaymentMethod
varchar
TransactionDate
datetime
TransactionDetails
Field
Type
DetailID
int
TransactionID
int
ProductID
int
Quantity
int
Subtotal
decimal
Inventory
Field
Type
InventoryID
int
ProductID
int
StockIn
int
StockOut
int
LastUpdated
datetime
ERD (Entity Relationship Diagram)
Plain text
Users
------
UserID (PK)
Username
Password
Role

Categories
-----------
CategoryID (PK)
CategoryName

Products
---------
ProductID (PK)
CategoryID (FK)
ProductName
Price
StockQuantity
ProductImage

Customers
----------
CustomerID (PK)
CustomerName
PhoneNumber

Transactions
-------------
TransactionID (PK)
CustomerID (FK)
TotalAmount
PaymentMethod
TransactionDate

TransactionDetails
------------------
DetailID (PK)
TransactionID (FK)
ProductID (FK)
Quantity
Subtotal

Inventory
----------
InventoryID (PK)
ProductID (FK)
StockIn
StockOut
LastUpdated
Relationships
Plain text
Categories (1) ---- (Many) Products

Customers (1) ---- (Many) Transactions

Transactions (1) ---- (Many) TransactionDetails

Products (1) ---- (Many) TransactionDetails

Products (1) ---- (Many) Inventory
Event-Driven Programming Concepts Used
Event
Description
Button Click
Purchase item
TextChanged
Search products
ComboBox SelectedIndexChanged
Filter category
Timer Tick
Auto stock checking
DataGridView CellClick
Show product details
Form Load
Load database data
KeyPress
Validate input
Advanced Features
Suggested Features
QR Code payment simulation
Barcode scanner simulation
Receipt printing
Dark mode
Low stock alert
Product recommendation
Sales analytics chart
Membership points
Multi-language support
Simple UI Design Ideas
Theme
Modern vending machine interface
Dark blue + white theme
Rounded buttons
Suggested WinForms Controls
Control
Usage
Panel
Layout
FlowLayoutPanel
Product cards
PictureBox
Product images
DataGridView
Tables
Chart
Sales graph
Timer
Real-time update
ProgressBar
Payment loading











erd 

Here's a complete visual breakdown of your QuickServe Vending Machine System design document, covering:
System Overview widget includes:

Tech stack (C#, WinForms, Visual Studio 2026, SQL Server)
All 9 forms color-coded by role — green for customer-facing, red/coral for admin-only, cyan for the entry point
Event-driven programming table with all 8 key event types and their handlers
Full 6-table database schema with PK/FK badges
Advanced features list

ERD diagram shows all 6 entities with their fields and relationships using crow's foot notation — CATEGORIES → PRODUCTS, CUSTOMERS → TRANSACTIONS, TRANSACTIONS → TRANSACTION_DETAILS, PRODUCTS → TRANSACTION_DETAILS, and PRODUCTS → INVENTORY.
Some implementation tips as you build this:

For the timer1_Tick low-stock check, set the interval to something like 30,000ms (30 seconds) and query WHERE StockQuantity < 5
The Payment Form balance calculation (balance = cash - total) should validate that cash >= total before enabling the confirm button
Use a FlowLayoutPanel with AutoScroll = true for the product grid — it handles dynamic card layout cleanly
Store ProductImage as a relative file path (e.g. images/cola.png) rather than binary in the DB for better performance
