# webscraping_db_functions

This is short tutorial how to use Azure Functions to load data from the internet and store it in a mssql database.

## Requirements

- _pyodbc_ \
  To install Microsoft ODBC driver 18 for SQL Server on macOS, run the following commands:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
HOMEBREW_ACCEPT_EULA=Y brew install msodbcsql18 mssql-tools18
```

- Create the database \
  https://learn.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart?view=azuresql&tabs=azure-portal \
  Here's a list of basic operations: https://learn.microsoft.com/en-us/sql/connect/python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc?view=sql-server-ver16 \
  I used Azure Data Studio to maintain the database using a tutorial like this to install everythin https://builtin.com/software-engineering-perspectives/sql-server-management-studio-mac
- Python requirements
  - azure-functions
  - pyodbc
  - requests
  - bs4
- Azure Functions
  - https://learn.microsoft.com/en-us/azure/azure-functions/create-first-function-vs-code-python
  - As I used a time trigger function, that runs every second you can find some tutorials in the internet
  - Also I used a http trigger function, that runs, when the "action" is set to "load"
- Energy Info API \
  https://api.energy-charts.info/

## Code Explanation

This example is a function, that runs every minute and collects the data from the API and stores it in the database. \
Theres no deeper sense in it as it is just for practice. \
I also put in the .py and .ipynb code to see where I started. \
I first did the webscraping part. Afterwords I managed the connection to the mssql database and lastly I put it in an Anzure Function.
