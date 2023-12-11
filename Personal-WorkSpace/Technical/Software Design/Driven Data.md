Driving Consistent Behaviour in .NET Using the Unit of Work Pattern

In this article we will explore how the Unit of Work pattern can be used to improve data consistency and drive additional cross-cutting behaviours in our .NET applications. We will implement Unit of Work in an Entity Framework ASP.NET API, and use it to decouple behaviours such as Event handling and Auditing of changes from our core Business Logic.
Unit of Work

In modern systems we generally need to read and write data across lots of different database tables when handling any given HTTP request. A Unit of Work can be used to group and commit all database write operations for a request into a single atomic transaction. This ensures that all grouped operations either pass or fail together.

Having a Unit of Work abstraction wrapped around all database changes provides a few benefits:

**Data Consistency**: Grouping all operations into a single transaction ensures that our data does not become out of sync. This can happen if some operations pass and some fail in a single request.
**Performance**: Reduced round trips to the database.
**Single Integration Point**: Database changes are committed from a single place. This simplifies our code and also provides a single point that we can use to integrate additional behaviours for our applications.

The starting point of the implementation uses a generic Repository for saving database changes. However, there are some issues with this approach. It is possible for the insertion of a WeatherForecast to succeed while the insertion of a WeatherAlert fails, leading to inconsistent data. Additionally, every time a WeatherAlert is created, the code must also include sending an alert notification, which can fail independently.

To address these issues, the content introduces the Unit of Work pattern. The Unit of Work allows grouping of database operations into a single atomic unit. In this implementation, Entity Framework's ChangeTracker is used to collect all changes to entities. Calling SaveChanges on the DbContext commits all uncommitted changes in a single transaction.

The Unit of Work is injected as a scoped service, ensuring it has the same lifetime as the DbContext and Repository instances. When CommitAsync is called, both the WeatherForecast and WeatherAlert entities are committed to the database simultaneously.

The Repository implementation allows adding and removing entities linked to the ChangeTracker but doesn't handle committing changes to the database. This responsibility lies with the Unit of Work. The Entity Framework ChangeTracker keeps track of all changes, allowing them to be committed by the Unit of Work.

Lastly, the content highlights that the Unit of Work can be used to drive additional cross-cutting behaviors in the application, further improving its functionality.


A better approach is to have the weather alert entity publish an event when it is created, and have an event handler responsible for sending the weather alert. This way, it doesn't matter where the entity is created, the event will always be published and handled in the same way.

To publish events from an entity, the "delayed dispatch" technique is used. Events are added to the entities and dispatched/published later. The UnitOfWork is the ideal place to hook into for publishing any domain events raised by the entities. Before committing the database changes, the UnitOfWork can extract any domain events raised by the entities in the Entity Framework DbContext ChangeTracker and publish them.

The **DispatchEventsAsync** method is used to check for domain events in tracked entities and handle them. It uses a while loop to handle any additional domain events raised from the event handlers. MediatR is used to publish and handle the domain events in the same process.

By decoupling the sending of weather alerts through events, the application becomes more flexible and scalable, as any additional areas in the application that create weather alert entities will automatically publish the necessary events for sending alerts.

**Outbox Pattern**
Our application is much more decoupled and flexible now that we have added Event Handling through our UnitOfWork. We could still run into problems if:

Sending Alerts via our NotificationService fails. This will throw an Exception before our database changes can be Committed
Sending an Alert is successful but Committing our database changes fails

Luckily we can use Integration Events and the Outbox pattern to handle both of these cases!

When using the Outbox pattern, we treat Integration Events as Entities in our database and persist them when the parent transaction that produced them is Committed (1). This way we ensure that the Integration Events are always persisted if the transaction succeeds and not persisted if it fails.

A separate service is created to read queued Integration Events from the database (2) and Publish them via a Message Broker (3). When the Integration Event is successfully published, it is removed from the database. If the Message Broker is down then the service will keep trying to publish the events until it is back online.
Transactional Outbox Pattern

An additional Background Service process would need to be run to Subscribe to Integration Events from the Message Broker.

I have written a previous article about handling Integration Events using the Outbox pattern, no surprises it uses a UnitOfWork to do so: https://betterprogramming.pub/domain-driven-design-domain-events-and-integration-events-in-net-5a2a58884aaa
Other Behaviours

There are lots of other behaviours that could also be driven from your UnitOfWork. The UnitOfWork creates a single point that we can use to implement some of those behaviours, without needing to make lots of changes to your application.

Here’s a few additional behaviours that I have seen implemented through Unit of Work:

Database Auditing can be achieved through the Entity Framework ChangeTracker as well. Here is an example of how: https://levelup.gitconnected.com/net-audit-implementation-via-the-entity-framework-change-tracker-3436854fd613
Logging
Telemetry and Metrics
Email and Notification Scheduling/Outbox
Exception Handling
Retry Logic and Circuit Breaking
Custom Transactions and Rollback. This is helpful if you aren’t using Entity Framework