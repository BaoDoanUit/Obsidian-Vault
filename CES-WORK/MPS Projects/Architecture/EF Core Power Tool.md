Generate script via EF Core Power Tool
Idea for using EF to bulk Insert

1. Get Data Input 
- Can use global varible
- Read file Csv (Open SFTP) or FTP
2. Validate Data 
- Verify column header
- Verify data before add to List Model
- Get Info Validation (Open Connection) -> (Close Connection)
3. Return Final Model 
- Calculate 
- Aggregate
- Extract data model
4. Split object to bulk insert
- Filter List Model
- Bulk insert (Open Connection)
- Return message (Close Connection)

