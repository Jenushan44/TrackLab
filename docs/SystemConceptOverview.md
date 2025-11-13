# System Concept Overview 

## 1. Enterprise Description 
PriceMatchr is a system that is designed to help users compare product prices across multiple Canadian retailers. The system collects product information, stores price updates from different stores and shows users where they can find the lowest price at any moment. The goal  is to reduce the time users spend checking websites individually and provide a simple tool to view all prices in one place. 

## 2. Persistent Data 
The system needs to store long-term data that remains in the database until it is intentionally changed or removed. 
PriceMatchr will use persistent data for: 
- Product Information (name, brand, category)
- Retailer information (store name, location)
- Price records (product, retailer, price, date collected)
- Matched deals (lowest prices found by the system)
- User search history or saved items 

## 3. Why a Database is needed 
Using a database makes the project more reliable and easier to maintain. PriceMatchr benefits from a DBMS because: 
- Shared data is used across search, comparisons and analytics
- Reduced redundancy keeps the data consistent
- Integrity rules ensure price updates remain accurate
- Security controls restrict who can modify key information

## 4. System Users 
PriceMatchr interacts with multiple types of users: 
- End users: Search for deals and view comparisons
- Application Developers: Build and improve the system
- Database Administrator: Maintains the database
- Data Administrator: Decides what data is needed and sets data policies 

## 5. Schema and Instance 
In PriceMatchr, the schema describes the permanent structure of the database. This includes how products, retailers and price records are organized along with the fields each of these items contains. The schema does not change often. 

An instance shows the actual data stored in the database at a specific moment. For example, the current list of products, the latest price updates or newly added retailers. Whenever price data is refreshed or new items are added, the instance changes while the schema stays the same.

## 6. Three-Level Architecture 

### External Level 
This level represents how users view the system. In PriceMatchr, this includes search results, price comparison views and deal summaries. Users only see the information they need without being exposed to the full database. 

### Conceptual Level 
This level describes the overall logical structure of the database. It includes the main entities such as products, retailers and price records along with the relationships between them. This forms the combined view of all data in the system. 

### Internal Level
This level focuses on how the data is physically stored. In PriceMatchr, this includes file organization, indexes that speed up searching and how price data is arranged on disk. These details are hidden from users and application developers. 

## 7. Data Independence 

### Logical Data Independence 
Changes to the logical structure should not require changing user views. In PriceMatchr, adding a new product attribute or introducing categories should not affect search results or comparison pages. 

### Physical Data Independence
Changes to how data is stored should not require modifying the logical design.For example, adding indexes to improve performance or reorganizing how price data is stored should not affect how the system's entities and relationships are defined. 

## 8. System Components 

### DDL (Data Definition Language) 
DDL will be used to define the tables and structure for products, retailers and price records. It handles the creation of keys, constraints and the overall schema. 

### DML (Data Manipulation Language) 
DML will be used to insert, update, delete and retrieve data. PriceMatchr will use DML to refresh price data, add new products and display comparisons. 

### Database Administration 
Managing PriceMatchr's database includes maintaining performance, handling security and access control, ensuring data integrity and managing backups and recovery. These responsibilities ensure the system remains reliable as more data is added. 
