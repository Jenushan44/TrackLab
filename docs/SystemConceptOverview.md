# System Concept Overview 

## 1. Enterprise Description 
PriceMatchr is a system that is designed to help users compare product prices across multiple Canadian retailers. The system collects product information, stores price updates from different stores and shows users where they can find the lowest price at any moment. The goal  is to reduce the time users spend checking websites individually and provide a simple tool to view all prices in one place. 

## 2. Persistent Data 
The system needs to store long-term data that remains in the database until it is intentionally changed or removed. 
Pricematchr will use persistent data for: 
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
