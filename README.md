# webscraping_db_functions

This project demonstrates how to use **Azure Functions (Python)** to fetch data from the internet (via the [Energy Charts API](https://api.energy-charts.info/)) and store it in an **Azure SQL Database (MSSQL)**.

It’s intended as a practice example for combining web scraping, database operations, and Azure Functions.

---

## Requirements

### 1. Python dependencies
Install the Python libraries used by the function:

```bash
pip install -r requirements.txt
```

### 2. ODBC driver (for pyodbc)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
HOMEBREW_ACCEPT_EULA=Y brew install msodbcsql18 mssql-tools18

### 3. 
You need an Azure SQL Database.
Follow this tutorial to create one:
👉 Create a single database in Azure SQL Database [portal](https://learn.microsoft.com/de-de/azure/azure-sql/database/single-database-create-quickstart?view=azuresql&tabs=azure-portal&utm_source=chatgpt.com)  
To manage your database:
Use Azure Data Studio (cross-platform) or SSMS (Windows).
Helpful tutorial: [Install & use Azure Data Studio](https://learn.microsoft.com/de-de/azure-data-studio/download-azure-data-studio?utm_source=chatgpt.com&tabs=win-install%2Cwin-user-install%2Credhat-install%2Cwindows-uninstall%2Credhat-uninstall)

### 4. Azure Functions Core Tools
Install [Azure Functions Core Tools](https://learn.microsoft.com/de-de/azure/azure-functions/functions-run-local?utm_source=chatgpt.com&pivots=programming-language-csharp) v4 so you can run & debug functions locally.
In VS Code, also install:
Azure Functions extension
Python extension

### 5. Configuration
Create a file config.py in the project root with your DB connection info:
````
database_config = {
    'server': 'your-sql-server-name.database.windows.net',
    'database': 'EnergyChartsDB',
    'username': 'your-username',
    'password': 'your-password',
    'driver': '{ODBC Driver 17 for SQL Server}'  # or 18 if installed
}
````

### 6. Run locally
`````
func host start
`````

#### 7. Trigger Function
````
curl "http://localhost:7071/api/webscrapingHTTP?action=load"
````
