# Warehouse Management System

This project is a comprehensive Warehouse Management System (WMS) designed to oversee the flow of goods from suppliers to warehouses, and further to retail shops and points of sale. It manages inventory, orders, deliveries, transactions, and more.

## Features

- Manage products, categories, and product metadata
- Track users and their orders
- Handle deliveries and addresses
- Manage transactions and transaction types
- Support for product-category relationships (many-to-many)
- Extensible schema for future enhancements

## Database Schema

The system is built on a relational database schema. Below is a summary of the main tables and their relationships.

### Entity-Relationship Diagram (ERD)

```plaintext
+----------------+      +-------------------+      +------------------+
|    Users       |      |     Category      |      |  TransactionType |
+----------------+      +-------------------+      +------------------+
| userID (PK)    |      | categoryId (PK)   |      | transactionTypeID|
| ...            |      | ...               |      | (PK)             |
+----------------+      +-------------------+      +------------------+
         |                       |                           |
         |                       |                           |
         |                       |                           |
         |                       |                           |
         v                       v                           v
+----------------+      +-------------------+      +------------------+
|     Order      |<-----| ProductCategory   |----->|    Product       |
| orderID (PK)   |      | categoryId (FK)   |      | productId (PK)   |
| userID (FK)    |      | productId (FK)    |      | ...              |
+----------------+      +-------------------+      +------------------+
         |
         v
+------------------+
|   OrderItem      |<--------------------+
| OrderItemId (PK) |                     |
| orderId (FK)     |                     |
| productId (FK)   |                     |
| ...              |                     |
+------------------+                     |
         |                               |
         v                               |
+------------------+                     |
|   StockItem      |---------------------+
| itemId (PK)      |
| ...              |
+------------------+

+------------------+      +------------------+
|    Address       |      |    Delivery      |
+------------------+      +------------------+
| addressID (PK)   |      | deliveryID (PK)  |
| orderID (FK)     |      | orderID (FK)     |
| ...              |      | addressID (FK)   |
+------------------+      +------------------+

+------------------+
|   Transaction    |
+------------------+
| transactionID(PK)|
| orderID (FK)     |
| transactionTypeID|
| ...              |
+------------------+
```

## Setup

1. Clone the repository.
2. Run the SQL scripts in `/DB Schema` to create the database and tables.
3. (Optional) Use the scripts in `/Insert Queries` to populate sample data.
4. Configure your database connection as needed for your environment.

## Usage

- Use this system to manage warehouse operations, inventory, and sales.
- Extend the schema for custom needs (e.g., more user roles, advanced reporting).

## Directory Structure

- `DB Schema/` — SQL scripts for schema creation
- `Insert Queries/` — Sample data insertion scripts
- `Functions/`, `Procedures/`, `Triggers/` — Advanced database logic
- `README.md` — Project documentation

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

## License

[MIT License](LICENSE) (or specify your license)
