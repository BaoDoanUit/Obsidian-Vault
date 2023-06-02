##### Process 1: Load Hedge Data and extrapolate at the hourly interval level:

1) WE will have 2 C# with windows task (.Net 7 EF 7)
- One will read the files daily/on demand and populate the queue of Hedge data that needs to be converted (MPS.HedgeData.FileProcessor) 
- Second will read from the queue, convert to interval level and populate the table (MPS.HedgeData.QueueConsumer)
- UI trigger will insert messages into the same queue for processing

<mark style="background: transparent;">General Process</mark><mark style="background: transparent;">![[MPS-General-1.png]]</mark>

##### Process 2:


