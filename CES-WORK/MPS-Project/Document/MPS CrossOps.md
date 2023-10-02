##### Process 1: Load Hedge Data and extrapolate at the hourly interval level:
 1. WE will have 2 C# with windows task (.Net 7 EF 7)
- One will read the files daily/on demand and populate the queue of Hedge data that needs to be converted (MPS.HedgeData.FileProcessor)
- Second will read from the queue, convert to interval level and populate the table (MPS.HedgeData.QueueConsumer)
- UI trigger will insert messages into the same queue for processing

General Process![[MPS-General-1.png]]



##### Process 5: Calculate positions
**Information**
- This process will calculate position hourly, monthly and HE level
- This will be an upsert by taking backup of current position data

**Architecture**
- C# based process with windows task (.Net 7 EF 7))
	- MPS.Position.PositionsHouly
	- MPS.Position.PositionsMonthly
	- MPS.Position.PositionsByHE
- Queue up position request from command cernter. Command Center screen will be connected to the azure service bus queue
- C# consumer will pull requests from the queue and process the data.
- Can have different queues/instances for different company/clients for scaling
- In future, determine the input (or trigger) and populate the queue without manual intervention.
![[Pasted image 20230612105241.png]]

#### Processes
![[Pasted image 20230612122212.png]]

