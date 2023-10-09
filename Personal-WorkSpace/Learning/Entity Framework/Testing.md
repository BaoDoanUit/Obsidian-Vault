Time To Live (TTL) feature.

Consider about how to implement in the real world?

Trade-off
But the challenge is that adding TTL to big tables will bring a heavy load to the background scanner and might result in an outage. Their solution is to only add a TTL attribute to the new items in the table. The retention period of their DynamoDB data is three months.


![[../../../Gallery/0 pA8RDirVbaGHH_4Z.webp]]

Even if Kafka can provide 99.95% SLA, there is still the chance of stream producer failures. When the producer fails, they will store the message in an Amazon Simple Queue Service (SQS) and retry. If the retry also fails, it will be moved to the SQS dead letter queue (DLQ), to be consumed at a later time.


BENEFIT
- In terms of stability, they use DynamoDB as the critical OLTP database to ensure high availability for online order processing.
- Scalability wise, they use RDS as the OLAP database to support their quickly evolving business requirements by using a rich, multiple index.
- Cost efficiency is achieved by data retention in both databases. For consistency, they built a single source of truth OLTP database and an OLAP database that is eventually consistent with the help of the data ingestion pipeline.


