
Sqoop incremental load is used to import only the new or updated records from a relational database to Hadoop, instead of importing the entire dataset every time. This approach can significantly reduce the amount of data transferred and the time required for the import process. 

Here’s a basic overview of how to perform an incremental load with Sqoop:

### 1. Choose the Incremental Load Mode
Sqoop supports two modes for incremental loading:
- **Append Mode**: Used when new rows are added to the source table.
- **Lastmodified Mode**: Used when rows in the source table are updated.

### 2. Prepare Your Table
Ensure your source table has a column that can be used to track new or modified records. For example, this could be a timestamp column for the `Lastmodified` mode, or an auto-incremented primary key for the `Append` mode.

### 3. Use the Sqoop Import Command
The basic syntax for the Sqoop import command with incremental load is:

#### For Append Mode:
```bash
sqoop import \
  --connect jdbc:mysql://localhost/dbname \
  --username user \
  --password pass \
  --table tablename \
  --incremental append \
  --check-column id_column \
  --last-value last_imported_value \
  --target-dir /path/to/hdfs/dir
```
- `--check-column` is the column to check for new records.
- `--last-value` is the last value imported (from the previous import).

#### For Lastmodified Mode:
```bash
sqoop import \
  --connect jdbc:mysql://localhost/dbname \
  --username user \
  --password pass \
  --table tablename \
  --incremental lastmodified \
  --check-column last_modified_column \
  --last-value last_imported_value \
  --target-dir /path/to/hdfs/dir
```
- `--check-column` is the column that indicates the last modification time.

### 4. Schedule the Job
To perform incremental loads regularly, you can schedule the Sqoop job using a scheduler like Apache Oozie or cron.

### Example Use Case
Suppose you have a table `sales_data` with a column `sale_date` that indicates when a record was last updated. You can use the `lastmodified` mode to import only the records that have been updated since your last import.

By setting up an incremental load, you ensure that only the necessary data is processed, making your ETL process more efficient and faster.