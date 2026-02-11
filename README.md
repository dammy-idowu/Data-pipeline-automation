## 🚀 Professional Data Pipeline & Real-Time Analytics Dashboard
A production-grade ETL (Extract, Transform, Load) pipeline built with Python, SQL, and Aiven Cloud PostgreSQL. This project automates the extraction of "dirty" enterprise data, performs complex cleaning (deduplication, standardization, imputation), and monitors business health through a real-time visualization dashboard with automated alerting.

## 🏗️ Architecture & Features
1. Cloud Infrastructure: Hosted on Aiven PostgreSQL for high availability and secure SSL connections.<br>
2. Automated ETL: A modular DataPipeline class using SQLAlchemy to handle complex joins and data cleaning logic.<br>
3. Intelligent Transformation:<br>
- Deduplication: Merges redundant customer and transaction records.<br>
- Standardization: Fixes casing errors (e.g., BOB SMITH → Bob Smith) and trims whitespace.<br>
- Imputation: Handles missing emails and orphan support tickets using professional business logic.<br>
- Real-Time Monitoring: A Seaborn & Matplotlib dashboard refreshing every 30 seconds.<br>
- Job Scheduling: Background task orchestration via APScheduler running every 10 minutes.<br>
- Reliability & Alerting: An SMTP Alerting System that triggers email notifications on database connection failures or pipeline crashes.<br>

## 🛠️ Technology Stack
|**Category** |	**Tools** |
| :--- | :---- |
|Language |	Python 3.10+|<br>
|Database	| PostgreSQL (Hosted on Aiven Cloud)|<br>
|Orchestration |	APScheduler|<br>
|Data Processing |	Pandas, NumPy|<br>
|Database Toolkit	| SQLAlchemy, Psycopg2<br>
|Visualization |	Matplotlib, Seaborn|<br>
|Security |	python-dotenv (Environment Variables), SSL/TLS Encryption|<br>

## 📂 Project Structure
text
├── .env                # Secret credentials (Database URI, SMTP details)<br>
├── .gitignore          # Excludes .env and caches from version control<br>
├── main.ipynb          # The Jupyter Notebook containing the end-to-end pipeline<br>
├── requirements.txt    # List of required Python libraries<br>
└── README.md           # Professional project documentation<br>


## ⚙️ Setup & Installation
1. Database Setup<br>
- Create a free PostgreSQL instance on Aiven.io.<br>
- Obtain your Service URI.<br>
  
2. Environment Configuration<br>
- Create a .env file in the root directory:<br>
AIVEN_SERVICE_URI=postgresql+psycopg2://avnadmin:password@host:port/defaultdb?sslmode=require<br>

3. Installation<br>
- pip install -r requirements.txt


## 📈 Pipeline Execution Logic
1. Seed: The script generates 20 rows of "Dirty Data" (duplicates, nulls, casing errors) and pushes them to the cloud.<br>
2. Extract: The pipeline executes an optimized SQL query against the raw_enterprise_data table.<br>
3. Transform:<br>
- Cleans customer_name using .str.title().str.strip().<br>
- Imputes missing ticket_id and status.<br>
- Flags negative amount values as is_refund.<br>
- Visualize: The dashboard updates every 30 seconds to show the latest Revenue Trends and Support Ticket Volume.<br>
- Monitor: If the Aiven connection drops, the send_alert function dispatches an emergency email.<br>

## 🛡️ Security Best Practices
- Credential Masking: No passwords are hardcoded; all secrets are managed via os.getenv.<br>
- Database Safety: Connection pooling is implemented with pool_pre_ping=True to handle serverless timeouts gracefully.<br>
- Error Handling: The system uses try-except blocks to "fail loudly" via logs and emails without crashing the main application.<br>

## 👨‍💻 Author
Damilola Idowu<br>
Full stack Data Analyst / Data Scientist<br>
[[[Your LinkedIn Profile Link](https://www.linkedin.com/in/damilola-idowu-contact-info)]] | damilolapeter.idowu@gmail.com
