# Setting Up Apache Airflow on WSL (Linux System)

This guide will help you set up Apache Airflow on a system running Windows Subsystem for Linux (WSL).

## Prerequisites

- WSL installed on your system
  
## Step 1: Install Dependencies

1. **Update and Upgrade WSL**:
   ```bash
   sudo apt update && sudo apt upgrade
   ```

2. **Install Required Packages**:
   ```bash
   sudo apt install python3 python3-pip python3-venv libpq-dev
   ```

## Step 2: Set Up a Python Virtual Environment

1. **Navigate to Your Project Directory**:
   ```bash
   cd /path/to/Minor Project
   ```
   Replace `/path/to/Minor Project` with the actual path.

2. **Create a Virtual Environment**:
   ```bash
   python3 -m venv airflow_env
   ```

3. **Activate the Virtual Environment**:
   ```bash
   source airflow_env/bin/activate
   ```

## Step 3: Install Apache Airflow

1. **Set Environment Variables**:
   ```bash
   export AIRFLOW_HOME=~/airflow
   ```

2. **Install Apache Airflow**:
   ```bash
   pip install "apache-airflow==2.7.0" --constraint "https://raw.githubusercontent.com/apache/airflow/constraints-2.7.0/constraints-3.8.txt"
   ```

## Step 4: Initialize the Airflow Database

1. **Initialize the Database**:
   ```bash
   airflow db init
   ```

## Step 5: Create an Admin User

1. **Create an Admin User**:
   ```bash
   airflow users create \
       --username admin \
       --firstname YOUR_FIRSTNAME \
       --lastname YOUR_LASTNAME \
       --role Admin \
       --email YOUR_EMAIL
   ```

   Replace `YOUR_FIRSTNAME`, `YOUR_LASTNAME`, and `YOUR_EMAIL` with your details.

## Step 6: Start the Airflow Web Server and Scheduler

1. **Start the Web Server**:
   ```bash
   airflow webserver --port 8080
   ```

2. **Open a New Terminal for the Scheduler** and activate the virtual environment, then:
   ```bash
   airflow scheduler
   ```

## Step 7: Access the Web Interface

- Open your browser and navigate to `http://localhost:8080`. Log in using the admin credentials you created.

## Step 8: Exit the Virtual Environment

To deactivate the virtual environment, use the following command:
```bash
deactivate
```

This will return you to the system's global Python environment.

---
