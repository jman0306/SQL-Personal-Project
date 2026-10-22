# ClipPay — SQL & Data Analytics Project

A personal data analytics project exploring payment transactions through PostgreSQL, SQL, Python, and Power BI. The project covers relational database design, CSV data ingestion, SQL querying, and business-oriented transaction analysis.

**Tech Stack:** PostgreSQL · SQL · Python · pandas · SQLAlchemy · Power BI

[View Repository](https://github.com/jman0306/SQL-Personal-Project) · [Jupyter Notebook](https://github.com/jman0306/SQL-Personal-Project/blob/main/ClipPay.ipynb)

---

## Table of Contents

- [Project Overview](#project-overview)
- [Objectives](#objectives)
- [Technology Stack](#technology-stack)
- [Database Design](#database-design)
- [SQL Analysis](#sql-analysis)
- [Power BI Reporting](#power-bi-reporting)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [Running the Project](#running-the-project)
- [Limitations and Considerations](#limitations-and-considerations)
- [Future Improvements](#future-improvements)
- [Disclaimer](#disclaimer)

## Project Overview

ClipPay is a personal portfolio project designed to practice relational database management and transaction data analysis in a simulated payment environment.

The project uses PostgreSQL to store structured data, Python to load CSV files and interact with the database, and SQL to explore transaction activity and answer business-oriented questions. A Power BI report provides a complementary visualization layer.

The workflow covers the following stages:

1. Create a PostgreSQL database.
2. Define relational tables and data integrity constraints using SQLAlchemy.
3. Import customer, merchant, payment method, and transaction data from CSV files.
4. Query and aggregate transaction data using SQL.
5. Explore customer spending, transaction amounts, merchant categories, and geographic patterns.
6. Present analytical results through Power BI reporting.

## Objectives

- Design a relational database with primary keys, foreign keys, and validation constraints.
- Integrate Python with PostgreSQL using SQLAlchemy.
- Load structured data from CSV files using pandas.
- Write SQL queries to retrieve, filter, join, and aggregate data.
- Analyze transaction activity across customers, cities, merchants, and time periods.
- Practice SQL concepts relevant to data analyst interviews.
- Use analytical outputs to support reporting and data-driven decision-making.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Database integration and data processing |
| PostgreSQL | Relational database management |
| SQL | Data retrieval, filtering, joins, and aggregation |
| pandas | CSV ingestion and tabular data handling |
| SQLAlchemy | Database connections, schema definitions, and SQL execution |
| python-dotenv | Environment variable management |
| Jupyter Notebook | Interactive development and SQL practice |
| Power BI | Data visualization and reporting |
| Git and GitHub | Version control and project hosting |

## Database Design

The project uses four relational tables.

| Table | Description | Key fields |
|---|---|---|
| `customers` | Customer information | `customer_id`, `age`, `city` |
| `merchants` | Merchant information and business categories | `merchant_id`, `merchant_name`, `category` |
| `payment_methods` | Payment methods associated with customers | `payment_method_id`, `customer_id`, `method_type` |
| `transactions` | Transaction records | `transaction_id`, `customer_id`, `merchant_id`, `payment_method_id`, `amount`, `transaction_date` |

### Relationships

- A customer can have multiple transactions.
- A merchant can be associated with multiple transactions.
- A customer can have multiple payment methods.
- Each transaction references a customer, a merchant, and a payment method.

### Data Integrity

The database schema includes:

- Primary keys to identify records.
- Foreign keys to connect related tables.
- `NOT NULL` constraints for required fields.
- `CHECK` constraints to enforce basic business rules, including customer age of at least 18 and positive transaction amounts.
- SQLAlchemy models to define the database structure in Python.

## SQL Analysis

The Jupyter notebook contains SQL exercises and analytical queries organized around practical data retrieval and reporting tasks.

### Data Exploration and Filtering

- Retrieve records with `SELECT`.
- Filter records with `WHERE`.
- Identify unique values using `DISTINCT`.
- Sort and limit results with `ORDER BY` and `LIMIT`.
- Filter data using multiple conditions.

### Aggregation and Business Metrics

- Count records and transactions.
- Calculate total, average, minimum, and maximum transaction amounts.
- Group results by customer, city, or merchant category.
- Filter aggregated results using `HAVING`.
- Calculate transaction counts and amounts above specified thresholds.

### Relational Analysis

- Combine customers and transactions using `JOIN`.
- Connect transaction records with merchant information.
- Analyze customer spending and transaction activity across different dimensions.

### Advanced SQL Practice

The notebook also includes business-oriented query exercises involving:

- Aggregate functions such as `COUNT()`, `SUM()`, `AVG()`, `MIN()`, and `MAX()`.
- Conditional logic with `CASE`.
- Subqueries and Common Table Expressions (CTEs), where used in the notebook.
- Date-based filtering and transaction analysis.
- Window functions for calculating metrics across groups without collapsing individual records, where implemented.

### Example Business Questions

- Which customers have the highest total spending?
- What are the transaction totals and maximum transaction amounts by city?
- Which merchant categories generate the highest sales value?
- How many transactions exceed a specified amount?
- How does transaction activity vary across dates?
- Which customers rank highest by total spending?

These questions demonstrate how relational data can be transformed into metrics for operational reporting and business analysis.

## Power BI Reporting

The repository includes a Power BI report (`Power BI.pbix`) and a folder of PDF report exports.

The report complements the SQL exercises by presenting transaction data in a visual format. Open the `.pbix` file in Microsoft Power BI Desktop to explore the report.

Power BI Desktop is optional if your goal is only to run the Python notebook and SQL queries.

## Project Structure

```text
SQL-Personal-Project/
├── ClipPay.ipynb
├── database.py
├── customers.csv
├── merchants.csv
├── payment_methods.csv
├── transactions.csv
├── Power BI.pbix
├── Reportes_PowBI_PDF/
└── .gitignore
```

| File or directory | Description |
|---|---|
| `ClipPay.ipynb` | Database initialization, schema creation, CSV ingestion, and SQL exercises |
| `database.py` | Reusable PostgreSQL connection configuration |
| `customers.csv` | Customer dataset |
| `merchants.csv` | Merchant dataset |
| `payment_methods.csv` | Payment methods dataset |
| `transactions.csv` | Transaction dataset |
| `Power BI.pbix` | Power BI report |
| `Reportes_PowBI_PDF/` | Exported Power BI reports |
| `.gitignore` | Git exclusion rules |

## Getting Started

### Prerequisites

Before running the project, install or configure:

- Python 3.10 or later.
- PostgreSQL.
- A PostgreSQL account with permission to create the project database.
- Jupyter Notebook.
- Microsoft Power BI Desktop, if you want to view the report.

### 1. Clone the Repository

```bash
git clone https://github.com/jman0306/SQL-Personal-Project.git
cd SQL-Personal-Project
```

### 2. Create a Virtual Environment

On Windows:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

On macOS or Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Python Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables

Create a `.env` file in the project root and add your local PostgreSQL credentials.

```dotenv
DB_USER=your_postgres_user
DB_PASSWORD=your_postgres_password
DB_HOST=localhost
DB_PORT=5432
```

Do not commit real passwords or other credentials to GitHub.

### 5. Initialize the Database

Start PostgreSQL and open `ClipPay.ipynb` in Jupyter Notebook.

Run the database creation and schema initialization cells in order. The notebook creates the `clip_pay` database and defines the four relational tables.

The PostgreSQL user must have permission to create databases. If `clip_pay` already exists, handle that condition before rerunning the database creation step.

### 6. Load the CSV Files

Execute the CSV ingestion cells in the notebook to read the four datasets with pandas and insert their records into PostgreSQL.

The CSV files must remain in the project directory unless you update their file paths.

**Important:** The current ingestion code uses `if_exists="append"`. Avoid rerunning the data-loading cells against populated tables unless you have reset the data or otherwise ensured duplicate records will not be inserted.

### 7. Run SQL Queries

Continue through the notebook to execute the SQL examples and inspect their results in pandas DataFrames.

To reuse the database connection in another Python file, import the engine:

```python
from database import engine

with engine.connect() as connection:
    print("Connected to clip_pay")
```

### 8. Open the Power BI Report

Open `Power BI.pbix` using Power BI Desktop to inspect the report.

If you want to connect Power BI directly to your local PostgreSQL instance, ensure that PostgreSQL is running and that the required database connection and credentials are configured in Power BI.

## Environment Variables

The `database.py` module uses `python-dotenv` to load connection settings from `.env`.

| Variable | Description | Example |
|---|---|---|
| `DB_USER` | PostgreSQL username | `postgres` |
| `DB_PASSWORD` | PostgreSQL password | Your local password |
| `DB_HOST` | PostgreSQL server host | `localhost` |
| `DB_PORT` | PostgreSQL server port | `5432` |

The database name is configured as `clip_pay` in `database.py`.

Keep `.env` excluded from version control. Only share placeholder values in documentation.

## Limitations and Considerations

- The project is designed for learning and portfolio demonstration rather than production payment processing.
- PostgreSQL must be installed and running locally for the database workflow to operate.
- Database creation requires sufficient PostgreSQL privileges.
- The CSV ingestion process appends records and should be handled carefully when rerunning the notebook.
- Power BI Desktop is required to inspect or modify the `.pbix` report.
- Analytical results depend on the supplied datasets and the queries executed.

## Future Improvements

Potential improvements include:

- Separate schema creation, data ingestion, and analysis into dedicated SQL and Python files.
- Add automated data quality checks and duplicate detection.
- Make database initialization and data ingestion safe to rerun.
- Add a `requirements.txt` file to standardize dependency installation.
- Document the database schema with an entity-relationship diagram.
- Include Power BI dashboard screenshots and clearly defined KPIs.
- Add a section with actual findings and quantified results from the analysis.
- Add automated tests for schema constraints and analytical queries.

## Disclaimer

ClipPay is an independent educational and portfolio project. It is not an official product or an internal system of any payment processing company. The datasets are provided for project analysis and should not be interpreted as verified production or customer data.
