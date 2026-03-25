# Airflow Docker ETL Pipeline

✅ Milestone 1: Weeks 1–2 Environment Setup & Pipeline Design

Configured Airflow Docker environment (docker-compose.yaml, config/airflow.cfg), defined ETL architecture, set up extraction scripts in dags/.

✅ Milestone 2: Data Cleaning & Transformation

Implemented data preprocessing using Pandas,
Applied:
Missing value removal
,Duplicate handling
Encoding (categorical → numerical),
Created derived features:
ExperienceLevel,
YearsInCompany

✅ Milestone 3: Weeks 5–6 Orchestration & Monitoring

Added Airflow DAGs (my_etl_dag.py, monitoring_dag.py) with scheduling, logging (logs/), Gmail alerts (EmailOperator).

✅ Milestone 4: Weeks 7–8 Dashboards & Deployment

Integrated dashboard framework (Streamlit/Dash ready), tested on production-scale datasets, finalized deployable framework.


#  Overview

This project implements a complete ETL pipeline using Apache Airflow to process employee data.

It includes automated data transformation and a real-time email alert system for monitoring pipeline execution.


# ⚙️ Key Features

- Automated ETL pipeline

- Data cleaning and preprocessing

- Feature engineering

- Email alert system:

- Single success notification (DAG level)

- Single failure notification (task level)

- Dockerized Airflow setup

- Persistent logs and data storage


#  Project Structure

airflow-project/

├── dags/

│   └── etl_pipeline.py          # Main ETL DAG

├── data/

│   ├── employee.csv            # Raw dataset

│   ├── data.csv                # Extracted data

│   └── transformed_data.csv    # Final processed data

├── logs/                       # Airflow logs

├── plugins/                    # Custom plugins (optional)

└── README.md


#  Architecture

employee.csv → extract → data.csv → transform → transformed_data.csv → load

                                   ↓
                              Email Alerts


 #  ETL Workflow
 
🔹 1. Extract

- Reads data from employee.csv

- Selects subset of data

- Saves to data.csv

🔹 2. Transform

- Removes missing values and duplicates

Encodes:

- Gender → (Male=1, Female=0)

- EverBenched → (Yes=1, No=0)

- Feature Engineering:

- ExperienceLevel

- YearsInCompany

Outputs: transformed_data.csv

🔹 3. Load

- Reads transformed data

- Displays processed output in logs


# 📩 Email Alert System

##  Implementation

- Integrated using SMTP (Gmail)

- Used Airflow callbacks:

- on_success_callback (DAG level)

- on_failure_callback (task level)


#  Behavior

- Scenario	Email

- All tasks success ✅	1 email

- Any task fails ❌	1 email


#  Key Design

- Avoided duplicate emails

- Implemented centralized notification logic

- Used reusable email function (DRY principle)


#  Technologies Used

- Python

- Apache Airflow

- Pandas

- Docker

- SMTP (Gmail)


#  How to Run

- docker-compose up -d

- Access Airflow UI:

http://localhost:8080


#  Testing

- Trigger DAG manually from UI

- Verify:

- Logs in logs/

- Output file transformed_data.csv

- Email alerts (success/failure)

 
 #  Output
 
 ## Cleaned and transformed dataset
 
 
<img width="1920" height="1080" alt="Screenshot 2026-03-25 232304" src="https://github.com/user-attachments/assets/80aafeac-1476-4360-8392-dce68f1aee47" />


## Automated monitoring via email alerts


<img width="1920" height="1080" alt="Screenshot 2026-03-26 000423" src="https://github.com/user-attachments/assets/fcfb139b-ac25-40fc-9079-1c5b5a61a9a1" />


#  Conclusion

This project demonstrates a production-ready ETL pipeline with automated data processing and intelligent alerting, ensuring reliability and maintainability.

#  License  
This project is released under the MIT License. See the `LICENSE` file for more information.  

Designed as a production-ready ETL framework, developed over an 8-week lifecycle, enabling reliable and scalable data workflows.








