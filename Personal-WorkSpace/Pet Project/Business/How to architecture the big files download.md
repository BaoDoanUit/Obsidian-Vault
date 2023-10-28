### Requirement
I have a website where new requirement came up where user can download a zip file of 500MB from the server. I am expecting max 10 concurrent users(CU) will be performing this activity . Webservers contains the files on same server.
- Current stats : Currently server 60 request per sescond with 99 percentile served with in 1 second . CPU/Memory stats are under utilized.Though I will get the performance benchmarking done here. But before development would like to know what factors I should consider to know below points
- What max extra memory and CPU these 10 Concurrent Request(CR) may use ?
- Can I serve it from existing web server only ? Or Ideally this should be catered through separate webservers ?
- what impact this use case can create on my existing traffic ?

### Analysis
**My understanding theoritically is**
- Considering 100 Mbps network speed average scenario at server side , it will take 40 sec just to transfer the bytes.
- Conidering HDD read spead i.e. 2 MB per sec on an average , it will take 250 secs(approx 5 minutes ) just to read the data from disk. Which means that 10 concurrent http thread will be continously working(primarily doing disk IOPS) for 5 mins . Is n't it ?
- CPU load may be fine as it is primarily disk io intensive ops. Extra memory load of 5 GB may be there for 10 CR . Right ?
- In case of more than 10 CR, I will take them in queue and process later.
- My final understanding is : If I store the files on separate server I can reduce the IOPS from current webserver , I may be good considering I get 5 GB of extra memory

>[!question] Just to want to get the solution/thoughts to design it correctly.