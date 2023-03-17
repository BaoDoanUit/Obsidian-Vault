#### Mapping 1 - 1 table (source - target)
- Table source (reference by primary key) (Materialized view) (Apply for the status of this objects change many times)
     - Has field changed (bit) 1 - 0 for picking data to synchronize 
     - Has field finish (bit)  1 - 0 never pick this item for synchronize
     - Consume all transactions changed impact to table source
- Table target (reference by primary key)
- Pros & Cons
     - Easy to inserting and updating new data change
     - Hard make table source consistency
- References
     - [Idea mapping 1 - 1](https://towardsdatascience.com/table-design-best-practices-for-etl-200accee9cc9?gi=71f1101c2509)
     - [Materialized View](https://dogy.io/2020/10/27/database-301-materialized-view/ )
     - [Oltp - Olap](https://dogy.io/2020/11/13/database-302-oltp-hay-olap/)

#### Partition mapping table -- (Transperiod time)
- If have combine key it should be better
- All transaction should be updated field "Modified Date" all table related?
     - Impact all current processes related 
- 

#### Bulk import (ETL) hoặc sử dụng event stream
- 

Conversation ETL
Here's my thoughts on your questions.

1) Warehouse Design:

Read Ralph Kimball's Book: The Data Warehouse Toolkit.

Your dimension table has a bunch of columns with meaningless names. Instead of field_5, the column should be given a name that has a business meaning. Data Warehousing is for ease of querying by business & reporting folks.

I don't see any fact tables here. Understanding what the user dimension will be used for is important in it's design.

2) The ETL Process

Have you identified where the bottleneck in the ETL process is? Is it on the reading of data from the source, the transformation of that data, or the writing to the database? You may be writing at 40,000 rows / sec but if you can only read 1,000 rows/sec from an XML data source, you're not going to get very far.

Have you considered loading the changed records to a stage table in the database first, without any transformation, then using SQL to transform and update the data? Often you'll find performance in the database is better than offloading the work to an ETL Tool.

3) It's very realistic to update a few million records daily, if the hardware can handle it. I think it's important to understand if you are just going for a Type 1 dimension where you just overwrite changes (in which case a delete change rows, and then insert, may be a better option than a update/else/insert).

If you are keeping history of changes in a type 2 dimension, you might want to consider snowflaking the fields you want to track changes on in a separate minidimension. Kimball discusses this technique when you have a very large "customer" dimension. You would then use a periodic snapshot fact table which would allow you to track the changes to the users over time.

4) Your friend's suggestion to create a primary key out of the natural business keys is not a good idea for a data warehouse environment. We create an integer surrogate key so we can include it in the Fact Tables, to keep them skinny, since they will be orders of magnitude larger than the dimension tables.

### A data pipeline
So it is a sequence of data processing steps. Due to *logical data flow connections* between these stages, each state generates an output that serves as an input for the following stage.

> [!quote]
> THERE is a data pipeline whenever there is data processing between points A and B

A data pipeline's three major parts are a source, a processing step or steps, and a destination. Data extracted from an exteranl API (a source) can be loaded into the data ware house (destination). This is an example of a most common data pipeline where the source and destination are different.
However, it  is not always the case, as destination-to-destination pipelines also exist.

For example, data can originate as a reference table in the data warehouse in the first place and then after some data transformation, it can land in a new schema, for example, in analytics to be used in reporting solutions.

There is always a data pipeline when data is processed between source and destination
![[Pasted image 20230206134914.png]]

Event data created by just one source at the back-end, and event stream built with Kinesis Firehose and Kafka stream, can feed a number of various destinations.

Consider user engagement data from Google Analytics as it flows as an event stream that can be used in both analytics dashboards for user activity and in the Machine learning (ML) pipeline for churn prediction.

Despite using the same data source, both pipelines operate independently and must successfully complete before the user can see the results.

Alternatively, data from two or more `source` locations can be aggregated into just one `destination`. For example, data from different payment merchant providers can be transformed into a revenue report for the Business Intelligence (BI) dashboard.

``` ad-quote
Data quality checks, data cleansing, transformation, enrichment, filtering, grouping, aggregation, and the application of algorithms to the data are frequent steps in data pipelines.
```

#### Architecture types and examples
Data pipeline architecture as a term might mean several things depending on the situation. In general, it can be split into **conceptual** (logical) and platform levels or architecture types.

The conceptually logical part describes how a dataset is processed and transformed from collection to serving, whereas **platform architecture** focuses on an individual set of tools and frameworks used in a given scenario, as well as the functions that each of them plays.

This is a **logical structure** of a data warehouse pipeline:
![[Pasted image 20230206135338.png]]

In this article I found a way to extract a real-time data from Firebase/Google Analytics 4 and load it in BigQuery: 
https://towardsdatascience.com/how-to-extract-real-time-intraday-data-from-google-analytics-4-and-firebase-in-bigquery-65c9b859550c

And this is a conceptual data lake pipeline example:
![[Pasted image 20230206135600.png]]

This is a platform level architecture example:
![[Pasted image 20230206135610.png]]

This is a very common pattern for many lake house architecture solutions. In this blog post I created a bespoke data ingestion manager that is triggered by new object events when they are created in Cloud Storage:
https://towardsdatascience.com/how-to-handle-data-loading-in-bigquery-with-serverless-ingest-manager-and-node-js-4f99fba92436

### Streaming
Application can trigger immediate response to new data events thanks to stream processing.

> [!quote]
> STREAMING is "must-have" solution for enterprise data

![[Pasted image 20230206135735.png]]





