Last meeting (2023/09/20) 
- Provide example for specific situation.
- Keep track the good thing.

Meeting (2023/10/18)
- Update the long term goal
- Add new skill to learn
- Add ticket number related TOMO skill

Endorsement
Working with [user’s name] has been a pleasure. They have demonstrated a strong ability to set and achieve goals, which is a testament to their hard work and dedication. Their ability to set realistic and achievable goals has been a valuable asset to our team. I highly recommend [user’s name] for their ability to set and achieve goals


 RETAIL-23617


Note Taking
How to solve Read/Write Operation
- Database Layer
Orchestration approach can also be implemented with asynchronous communication, where the Write service would send a message to the Queue owned by Read Service. In this case, the services are decoupled and there is almost zero impact on the response time. The only hit in this case is — everytime a new service needs to sync user data, there will be a change on the User service to send a message to the Queue owned by this new service. Plus, there is a coupling now at the message contract level. Write service has to understand which user attributes are needed by which service and form the message accordingly. And now, you also need to manage more moving parts in the form of Message Queues.
- Business Layer
Looking at all the approaches, the team decides to go with Event based data replication, ensuring there is no impact on the performance of the Write service and at the same time Write data replication can happen almost in real time. And with more services which need such a sync to happen, it can happen in parallel, without impacting the Write service.


Event Driven Architecture, The Hard Parts:
If it’s OK for your application to sometimes lose the Business domain events, causing data inconsistencies across services then you can absolutely ignore this, but if this is not the case, then you need to understand this anti-pattern well and fix it.
Dual Write Anti Pattern is a situation when a Domain service has a requirement to write data to 2 different systems (Data Storage, Event Broker, etc.) as part of a single logical business transaction to ensure Eventual Data Consistency across services but it cannot always guarantee that either both the data systems will be updated successfully or none will be updated.

```
try
{
  Start DB Transaction
  Write into DB
  Push Event to Event Broker
  Commit DB Transaction
}
catch()
{
  Rollback DB Transaction
}
```

**Only in the edge case**, when the Database transaction commit fails (and it can very well fail by the way), the requirement is not met. Event is written to Event Broker but Data is not saved in the Database.

Approach 1 — Publish the event after data is saved into the Database

Could create ordering issues with domain event publishing. For example — if Create Feed Post failed to published and User performed a delete on the same feed post which was successfully sent to the Downstream systems
If the event to be published later could not be saved into Durable storage because of some reason, then you have situations of events getting lost. You can also maintain a flag in the business record in the Database table if the event is synced or not, but with that you are kind of coupling your event publishing needs with the main business entity.

Approach 2 — Use Outbox Pattern

There is a guarantee that events will be published eventually to the Event Store
Will never be lost, even if Event Store is not available at the time of publishing the event
Ordering of the events can be ensured
Requirement of insert

![[../../Gallery/1 2uyLikWezFWaqNmzD3f68w.webp]]



QUESTION:
Serverless architecture promises flexibility, infinite scalability, fast setups, cost efficiency, and abstracting infrastructure allowing us to focus on the code. But does it deliver?

Emphasize Resilience

Apart from the classic resiliency strategies for unexpected outages from AWS (multi-AZ, multi-region, etc), in serverless, it’s important to have strategies in place from the beginning to mitigate all the issues if the various places that can go wrong, like:

Internal failures due to downstream services
Internal failures due to bugs (oops!)
Message payload failures
Orchestration failures
AWS throttling errors
AWS random errors (yes, they do occur)
Lambda timeouts

```
cost of lambda = memory * execution time ms
cost of lambda = memory * round_up(execution time ms, 100)
Was it actually more cost efficient than just running a couple of servers?
```
