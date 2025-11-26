# E-commerce Data Audit & Analytics Pipeline

![Oracle Database](https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white)
![PL/SQL](https://img.shields.io/badge/PL/SQL-black?style=for-the-badge&logo=oracle&logoColor=white)

## 📌 Project Overview

This project implements a robust data engineering solution for a retail e-commerce scenario ("Melhores Compras"). It focuses on two critical aspects of data management: **Security/Auditing** and **Business Intelligence**.

The solution allows for tracking sensitive credit card data changes using Oracle PL/SQL triggers (Change Data Capture) and analyzing delivery satisfaction metrics using a Snowflake Dimensional Model.

## 🏗️ Architecture & Modules

### 1. Database Auditing System (Oracle PL/SQL)
To ensure data integrity and compliance, an auditing mechanism was built to track changes in the Credit Card entity.
* **Technique:** Trigger-based Change Data Capture (CDC).
* **Logic:** A `FOR EACH ROW` trigger captures `INSERT`, `UPDATE`, and `DELETE` operations.
* **Features:**
    * Logs the exact timestamp and operation type.
    * Stores both **Old Values** (before update) and **New Values** (after update) for critical fields (Card Number, Client Name, Expiry).
    * Handles `NULL` logic dynamically based on the operation type.

### 2. Analytical Data Mart (Snowflake)
Designed a dimensional model (Star Schema) to support the "Delivery Satisfaction Index" analysis.
* **Modeling:** Physical Data Model designed for OLAP operations.
* **Goal:** Enable the business team to query delivery performance and customer feedback efficiently.

## 📂 Repository Structure

```text
/
├── sql/
│   ├── oracle_audit/
│   │   ├── 01_create_tables.sql      # DDL for Client and Log tables
│   │   ├── 02_create_trigger.sql     # The Core PL/SQL Audit Logic
│   │   └── 03_test_scenarios.sql     # DML commands to validate the trigger
│   │
│   └── snowflake_datamart/
│       ├── create_datamart.sql       # DDL for Dimensions and Fact tables
│       └── drop_datamart.sql         # Cleanup scripts
│
├── docs/
│   ├── audit_results_evidence.png    # Screenshot of the Log table after DMLs
│   └── dimensional_model.png         # Diagram of the Snowflake Data Mart
│
├── .gitignore
├── LICENSE
└── README.md

```

## 🚀 How to Run

### Prerequisites
* Access to an Oracle Database instance (On-premise or OCI Autonomous Database).
* Access to a Snowflake Account (Standard or Enterprise).

### Steps for Auditing Module (Oracle)
1.  **Setup:** Execute `sql/oracle_audit/01_create_tables.sql` to create the source and log tables.
2.  **Deploy Logic:** Execute `sql/oracle_audit/02_create_trigger.sql` to compile the PL/SQL trigger.
3.  **Test:** Run `sql/oracle_audit/03_test_scenarios.sql` to simulate data transactions (Inserts, Updates, Deletes).
4.  **Verify:** Query the `T_MC_CARTAO_CREDITO_LOG` table to view the audit trail.

### Steps for Data Mart (Snowflake)
1.  **Deploy Schema:** Execute `sql/snowflake_datamart/create_datamart.sql` in your Snowflake worksheet.
2.  **Analyze:** Use the tables `FATO_AVALIACAO_ENTREGA` combined with dimensions to run analytical queries.

## 👤 Author

**Caroline Moura Maia**

* [![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/caroline-maia-data)
* [![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/MaiaCaroline)


### 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---
##  Licença

Este projeto está sob a licença MIT. Veja o arquivo LICENSE para mais detalhes.

---

**Development of a PL/SQL auditing system (CDC) for transaction tracking and dimensional data modeling**  
