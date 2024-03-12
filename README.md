# db_cdc_enabler_config
Some Configuration to enable cdc from various databases

# SQL Server
```
--use corresponding database
USE db_name;
--Change user to sa
EXEC sp_changedbowner 'sa';
--enable cdc at db level
EXEC sys.sp_cdc_enable_db;

--enable cdc on selected table
EXEC sys.sp_cdc_enable_table
       @source_schema = N'dbo'
      ,@source_name = N'table_name'
      ,@role_name = NULL
      ,@capture_instance = N'db_name_table_name'
      ,@supports_net_changes = 1
      ,@filegroup_name = N'PRIMARY';

--check if cdc is active
SELECT * FROM cdc.change_tables;
````

# MYSQL (CloudSQL)

Configurein CloudSQL with do checklist on "Enable Point in Time Recovery" to enable bin-log.

# PostgreSQL
