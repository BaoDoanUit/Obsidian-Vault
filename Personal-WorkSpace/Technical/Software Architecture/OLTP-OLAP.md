In the early stages of database development, databases were mainly used for commercial transactional activities, such as selling goods, ordering from suppliers, and paying employee salaries. As databases became more widely used in various fields, the term "transaction" began to evolve, referring to a logical unit of work (insert, update, delete, or a group of operations) that can access and modify the contents of the database.

OLAP stands for Online Analytical Processing, and it is used for efficient data analysis. Unlike OLTP (Online Transaction Processing), OLAP systems work with large amounts of data and prioritize accurate and comprehensive analysis rather than transactional integrity. OLAP systems typically have a smaller user group, consisting of analysts or managers, and are not used for interactive transactions like OLTP systems in banking.


The primary activity in OLAP systems is data querying, often involving complex and time-consuming queries. In contrast, OLTP systems use common commands like INSERT, UPDATE, and DELETE and require fast response times. Here are some key differences between OLTP and OLAP:


### OLTP:
Primarily read-focused, working with a small number of records often accessed via key scans.
Emphasizes real-time transaction processing and demands fast response times.
Used by end-users through web applications or apps.
Represents current state data.

### OLAP:
Primarily aggregate-based, working with a large number of records.
Supports bulk imports (ETL) or event stream processing.
Used by internal analysts to support decision-making.
Represents historical event data.

The dataset sizes in OLTP range from gigabytes to terabytes, while in OLAP, they range from terabytes to petabytes. SQL is a flexible language that can cater to the basic needs of both OLTP and OLAP. Initially, many businesses ran both types on the same database, but they eventually realized the performance degradation and impact on end-user operations. In the 1990s, companies started transitioning to running OLAP on separate databases, known as data warehouses, to separate it from the OLTP system.


The term OLTP (Online Transaction Processing) emerged from this, and most business applications are built on these systems. OLTP focuses on its most important aspect, which is transactions (insert, update, delete), and only requires searching or querying a very small number of keys.


Over time, people started utilizing the available data for reporting, statistics, evaluating, and improving business models. However, OLTP is not suitable for this context: typically, statistical queries require scanning a large amount of data. Furthermore, OLTP doesn't need all the raw data, but rather specific columns to perform operations like sum, average, count, etc.


This led to the emergence of a new system model.