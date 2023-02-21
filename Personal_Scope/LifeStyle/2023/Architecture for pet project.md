> ## Planning
High priority 
- Back-End Side
- Infrastructure
- Front-End Side
     - Mobile app
     - Web app
>

## Hardware
1 local machine 
- 1 API Gateway (ngrok service)
- Multiple microservice inside (docker)  
- Build RabbitMQ 
- Database Server (IP Local) 


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

###  Phase 1
- Using all request-response through API-GateWay (Trigger if number of requests/min limitation use re-try)
- Mobile App use SQLiteDB for work-offline mode
- Push all request to RabitMQ


### Phase 2
- Scaling System
- Rent VPS x
- 

    
## Notes
Convert DB SQL -> PostgreSQL
https://www.convert-in.com/docs/mss2pgs/intro.htm
