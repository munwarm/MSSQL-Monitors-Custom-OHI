# New Relic MSSQL Monitors Custom OHI Installation

* Pre-requisites:
Before you try copying the custom OHI, please make sure that:

1.) New Relic Infra Agent is installed and 
2.) MSSQL OHI is installed, configured and working correctly

* Step 1:
Stop running the infrastructure agent - net stop newrelic-infra

* Step 2:
Copy mssql-monitors-config.yml file to C:\Program Files\New Relic\newrelic-infra\integrations.d folder

* Step 3:
Update database, username and password arguments in the config file (mssql-monitors-config.yml)
Note: Please make sure this user has access to the system tables/databases the SQL queries are setup to run against.

* Step 4:
Copy all 8 files listed below to C:\Program Files\New Relic\newrelic-infra\custom-integrations folder
mssql-monitors-definition.yml
mssql-monitors.ps1
SQLAgentHealth.sql
SQLServerDBMirrorStatus.sql
SQLServerDBStatus.sql
SQLServerDBUnsentLog.sql
SQLServerInstanceStatus.sql
SQLServerSyncHealth

* Step 5:
Start Infrastructure agent - net start newrelic-infra

Step 6:
Give the agent a few minutes to run and check data in Insights by trying these commands.
SELECT * FROM SQLAgentHealth SINCE 15 minutes AGO
SELECT * FROM SQLServerDBMirrorStatus SINCE 15 minutes AGO
SELECT * FROM SQLServerDBStatus SINCE 15 minutes AGO
SELECT * FROM SQLServerDBUnsentLog SINCE 15 minutes AGO
SELECT * FROM SQLServerInstanceStatus SINCE 15 minutes AGO
SELECT * FROM SQLServerSyncHealth SINCE 15 minutes AGO
