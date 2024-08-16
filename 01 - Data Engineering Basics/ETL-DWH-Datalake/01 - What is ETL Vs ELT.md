### ETL vs ELT
Both ETL and ELT are a series of processes that prepare data for analysis and additional processing to provide actionable business insights.

#### ETL
ETL stands for “extract, transform, load,” a combination of the three data engineering processes that move data from one database, multiple databases, or other sources to a unified repository. 

The three processes of ETL are: 
    <b>Extraction</b>, in which raw data is pulled from a source or multiple sources. Data could come from transactional applications, such as customer relationship management data from Salesforce or enterprise resource planning data, or Internet of Things sensors that gather readings from a production line or factory floor operation. Extracted data may be in several formats, such as relational databases, XML, JSON, etc.

    <b>Transformation</b>, in which data is updated to match organizational needs and data storage solution requirements. Transformation can involve converting all data types to the same format, cleansing by removing inconsistent or inaccurate data, combining data elements from multiple data models, pulling in data from other sources, and other processes. During transformation, rules and functions are applied and data cleansed to prevent including bad or non-matching data to the destination repository. 

    <b>Loading</b>, in which data is delivered and secured for sharing, making business-ready data available to internal and external users. This process may include overwriting the destination’s existing data.


#### ELT
ELT is a variation of ETL in which data is extracted and loaded before it is transformed. This sequence allows businesses to preload raw data to a place where it can be modified. ELT is more typical for consolidating data in a data warehouse, as cloud-based data warehouse solutions are capable of scalable processing. 


#### Similarities of ETL and ELT
Both ETL and ELT allow businesses to consolidate data from multiple databases and other sources into a single repository with data that has been properly formatted and qualified. This unified data repository provides simplified access for analysis and additional processing. It also provides a single source of truth, ensuring that all enterprise data is consistent and up-to-date.


### Advantages of ELT over ETL
Though re-ordering the steps of the traditional ETL series to ELT may seem a trivial change, loading data to its destination before transforming it does have several advantages over transform-then-load. The difference between ELT vs. ETL encompasses various dimensions, including flexibility, accessibility, scalability, data maintenance, loading times and more.

#### More flexibility, 
as ETL is traditionally intended for relational, structured data. Cloud-based data warehouses enable ELT for structured and unstructured data

#### Greater accessibility, 
as ETL is generally supported, maintained, and governed by organizations’ IT departments. ELT allows for easier access and use by employees

#### Scalability, 
as ETL can be prohibitively resource-intensive for some businesses. ELT solutions are generally cloud-based 

#### SaaS, 
available to a broader range of businesses

#### Faster load times, 
as ETL typically takes longer as it uses a staging area and system. With ELT, there is only one load to the destination system

#### Faster transformation times, 
as ETL is typically slower and dependent on the size of the data set(s). ELT transformation is not dependent on data size

#### Less time required for data maintenance, 
as data may need to be re-sourced and re-loaded if the transformation is found to be inadequate for the data’s intended purposes. With ELT, the original data is intact and already loaded should additional transformation be necessary