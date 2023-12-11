## Planning
High priority
Keep it simple
Back-End Side
Infrastructure
Front-End Side
     - Mobile app
     - Web app

## Hardware
1 local machine 
1 API Gateway (ngrok service)
Multiple microservice inside (docker)  
Build RabbitMQ 
Database Server (IP Local) 
Multiple BackEnd App serve for direct 
Caching Server Free 
- MongoDB (Storage data around 1 month)

Using Mobile App run background like worker for miniservices???
ClientMobileApp handle request via socket.io? (Transit Message)
Synchronize every 1 hour for new data manipulate
Send message to Message Queue for processing

## Data
Tracking every action on application
Behavior of users can gain the value 
Build a system for community and then using this for finding new income

### Planning
1) Phase 1
- Using all request-response through API-GateWay (Trigger if number of requests/min limitation use re-try)
- Mobile App use SQLiteDB for work-offline mode
- Push all request to RabitMQ
- Do multiple automation processes
2) Phase 2
- Scaling System
- Rent VPS x

    
## Notes
Convert DB SQL -> PostgreSQL
https://www.convert-in.com/docs/mss2pgs/intro.htm



### Planning:
The project has a high priority and focuses on keeping the implementation simple.

#### Back-End Side:
**Infrastructure**: The back-end side of the project consists of various components.
**Hardware**: The infrastructure includes one local machine, an API Gateway service (ngrok), and multiple microservices running inside Docker containers.
**RabbitMQ**: A message broker system called RabbitMQ is used for inter-service communication.
**Database Server**: The project utilizes a local database server for data storage.
**Multiple BackEnd App Servers**: Multiple servers are deployed to directly serve the back-end applications.
Caching Server: A free caching server is used to improve performance.

#### Front-End Side:
The project includes both a mobile app and a web app as part of the front-end side.
MongoDB:
MongoDB is used as the primary database for storing data, with a retention period of approximately one month.

**Mobile App**:
The mobile app is designed to run background tasks, acting as a worker for the microservices.

**Client Mobile App**:
Requests from clients are handled using socket.io, facilitating message transit.
Data manipulation is performed every hour to synchronize and process new data.
Messages are sent to a Message Queue for further processing.

**Data**:
The project tracks every action performed within the application.
The behavior of users is analyzed to derive valuable insights.
A system is being built to foster a community and explore potential income opportunities.