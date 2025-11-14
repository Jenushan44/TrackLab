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

## 9. Entity-Relationship Design
The ER design for PriceMatchr identifies the main objects in the system and how they relate to one another. This helps define the structure of the database before any tables are created. 

### 9.1 Main Entities 
The main entities required for PriceMatchr are: 
- **Product**: Includes information about an item being tracked. Attributes may include ProductID, name, brand and category.
- **Retailer**: Represents a store or seller that offers a product. Attributes may include RetailerID, store name and location.
- **PriceRecord**: Stores the price of a specific product at a specific retailer at a specific time. Attributes may include PriceRecordID, price and dataCollected.
- **UserSearch**: Stores queries or saved items from users. Attributes may include SearchID, query text and timestamp.

### 9.2 Relationships 

- **Product–PriceRecord**: A product can have many price records since its price changes over time and across retailers. Relationship: 1 Product -> Many PriceRecords   
- **Retailer–PriceRecord**: A retailer can update prices for many products. Relationship: 1 Retailer → Many PriceRecords
- **Product–Retailer**: A product can appear in many retailers, and a retailer can offer many products. This creates a many-to-many relationship.

### 9.3 Keys and Identifiers
Each entity must have a unique identifier:
- ProductID uniquely identifies each product.  
- RetailerID uniquely identifies each retailer.  
- PriceRecordID uniquely identifies each price update entry.

### 9.4 Attributes Overview
This is a simplified attribute list for each entity:
- **Product:** ProductID (PK), name, brand, category  
- **Retailer:** RetailerID (PK), storeName, location  
- **PriceRecord:** PriceRecordID (PK), productID (FK), retailerID (FK), price, dateCollected  
- **UserSearch:** SearchID (PK), userInput, timestamp  

### 9.5 ER Diagram Summary (Text Description)
The ER structure of Pricematchr can be thought of as:
- Product and Retailer are connected through PriceRecord.
- PriceRecord contains the foreign keys that link it to both Product and Retailer.
- A many-to-many relationship between Product and Retailer is broken down using PriceRecord.
- Each entity has a clear primary key to ensure every item can be uniquely identified.
