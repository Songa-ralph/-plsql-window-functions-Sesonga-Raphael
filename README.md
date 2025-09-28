# SQL window functions
Individual Assignment 1
-----------------------------------------------------------------------------------------------------------------------------------

## Assignment Overview
 this project Demonstrate the use of PL/SQL window functions by solving a realistic business problem,
 The purpose is to provide business insight showing : Top 5 products per region,Total monthly sales,Month ove month growth,Customer Quartiles and 3-month moving average

## Business challenges
Businesses struggles when they records many transactions it is hard to analyze:
* their top peerforming products per region.
* Running monthly total sales
* Month-over-month growth
* Aggregate customer spend and their behavior
## Businesses that could benefit from this projects
* Retail businesses.
* E-commerce Platforms.
* Restaurants
* financial services like(banks,insurance).

##  Success Criteria
1. Identify **Top 5 products per region/quarter** → `RANK()`  
2. Compute **Running monthly sales totals** → `SUM() OVER()`  
3. Analyze **Month-over-month growth** → `LAG()/LEAD()`  
4. Segment customers into **quartiles** → `NTILE(4)`  
5. Calculate **3-month moving averages** → `AVG() OVER()`
##  Result analyses
## Descriptive (What happened?)
* Top product per region:-some product shows strong demand patterns
* Sales trends: - Some months have peaks and drop
## Diagnostic (Why did it happen?)
* Region preferences:- some regions favors certain products
* competitions:- competitors can affect sales.
## Prescriptive (What next?) 
* Focus marketing on top perfoming product per region discontinue or re-strategize low performers.
* Replicate success of strong-performing regions in weaker markets through promotions.
##  Reference
1. Window function on PostgreSQL: https://www.postgresql.org/docs/current/tutorial-window.html
2. How to use window function on freecodecamp: https://www.freecodecamp.org/news/window-functions-in-sql/

## 🗄️ Database Schema
### Tables
- **customers**: stores customer info (`customer_id`, `name`, `region`)  
- **products**: product catalog (`product_id`, `name`, `category`)  
- **transactions**: sales records (`transaction_id`, `customer_id`, `product_id`, `sale_date`, `amount`)  

### ER Diagram
```mermaid
erDiagram
    customers ||--o{ transactions : "makes"
    products ||--o{ transactions : "contains"
    customers {
        int customer_id PK
        varchar name
        varchar region
    }
    products {
        int product_id PK
        varchar name
        varchar category
    }
    transactions {
        int transaction_id PK
        int customer_id FK
        int product_id FK
        date sale_date
        decimal amount
    }
