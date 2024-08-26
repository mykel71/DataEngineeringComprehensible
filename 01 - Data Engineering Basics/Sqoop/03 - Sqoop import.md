### Sqoop Imports

Sqoop import is a process that allows you to transfer data from a relational database into the Hadoop ecosystem, typically into HDFS, Hive, or HBase. This operation is highly optimized to handle large volumes of data and can be performed in parallel using multiple mappers.

### How Sqoop Import Works

1. **Initiation:** The import process is initiated using a command-line interface (CLI) where the user specifies the details of the source database and the target location in Hadoop.
  
2. **JDBC Connection:** Sqoop uses JDBC to establish a connection with the relational database.
  
3. **Metadata Fetching:** Sqoop fetches metadata about the table, such as column names, data types, and row count. This metadata is used to configure the MapReduce job that will perform the import.

4. **Splitting Data:** Sqoop divides the data into multiple splits, which are processed in parallel by mappers. The number of splits is usually determined by the number of mappers, which can be controlled by the `--num-mappers` parameter.

5. **MapReduce Job:** Each mapper processes a split, fetching the data from the database and writing it to the specified Hadoop location (HDFS, Hive, or HBase).

6. **Completion:** Once all mappers finish their tasks, the data import is complete and available for use in the Hadoop ecosystem.

### Common Sqoop Import Commands

#### Basic Import to HDFS

```bash
sqoop import \
--connect jdbc:mysql://localhost/dbname \
--username root \
--password your_password \
--table tablename \
--target-dir /user/hadoop/tablename \
--num-mappers 4
```

- **--connect:** JDBC URL for connecting to the database.
- **--username & --password:** Credentials for the database.
- **--table:** The name of the table to import.
- **--target-dir:** The HDFS directory where the data will be stored.
- **--num-mappers:** Number of mappers to use for the import process.

#### Import Data into Hive

```bash
sqoop import \
--connect jdbc:mysql://localhost/dbname \
--username root \
--password your_password \
--table tablename \
--hive-import \
--create-hive-table \
--hive-table hive_tablename \
--num-mappers 4
```

- **--hive-import:** Specifies that the data should be imported directly into a Hive table.
- **--create-hive-table:** Creates a new Hive table before importing data.
- **--hive-table:** The name of the Hive table where the data will be stored.

#### Incremental Import

```bash
sqoop import \
--connect jdbc:mysql://localhost/dbname \
--username root \
--password your_password \
--table tablename \
--target-dir /user/hadoop/tablename \
--incremental append \
--check-column id_column \
--last-value last_id_value \
--num-mappers 4
```

- **--incremental:** Specifies the type of incremental import (e.g., append, lastmodified).
- **--check-column:** The column used to identify new or modified rows.
- **--last-value:** The last value imported in the previous incremental import. Sqoop will import rows with values greater than this.

#### Importing Data with Data Compression

```bash
sqoop import \
--connect jdbc:mysql://localhost/dbname \
--username root \
--password your_password \
--table tablename \
--target-dir /user/hadoop/tablename \
--compress \
--compression-codec org.apache.hadoop.io.compress.GzipCodec \
--num-mappers 4
```

- **--compress:** Enables compression for the data being imported.
- **--compression-codec:** Specifies the compression codec (e.g., Gzip, Snappy).

#### Importing Specific Columns

```bash
sqoop import \
--connect jdbc:mysql://localhost/dbname \
--username root \
--password your_password \
--table tablename \
--columns "col1,col2,col3" \
--target-dir /user/hadoop/tablename \
--num-mappers 4
```

- **--columns:** A comma-separated list of columns to import.

### Advanced Features of Sqoop Import

1. **Boundary Query:** Customizes the query used to determine how to split the data. This is useful when the default splitting mechanism (based on primary keys) isn't efficient.

    ```bash
    --boundary-query "SELECT MIN(id), MAX(id) FROM tablename"
    ```

2. **Where Clause:** Restricts the data being imported by adding a WHERE clause to the SQL query.

    ```bash
    --where "column_name > 1000"
    ```

3. **Split-by Column:** Specifies the column that Sqoop should use to split the data for parallel import.

    ```bash
    --split-by id_column
    ```

4. **Null String and Null Non-String:** Defines how null values should be represented in the imported data.

    ```bash
    --null-string '\\N' \
    --null-non-string '\\N'
    ```

### Best Practices for Sqoop Imports

- **Use Parallelism:** Leverage the `--num-mappers` parameter to parallelize data transfer, but balance this with the load on the database.
- **Incremental Imports:** Use incremental imports to transfer only new or updated data, reducing the amount of data moved.
- **Compression:** Enable compression to save storage and reduce network usage, especially for large datasets.
- **Data Types:** Be cautious with data types; ensure that the types in Hadoop (Hive/HDFS) are compatible with those in the source database.
- **Boundary Queries:** Use custom boundary queries for efficient data splitting, especially for large tables.

### Conclusion

Sqoop import is a powerful feature for transferring data from relational databases into Hadoop. By using various options and configurations, you can optimize the process for different use cases, whether it's importing into HDFS, Hive, or HBase, handling incremental data, or ensuring data compression.
