EF Core or micro-ORM?
While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it isn’t the only choice. Another popular open-source alternative is Dapper, a so-called micro-ORM. A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures. In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data. Because it doesn’t abstract SQL from the developer, Dapper is “closer to the metal” and lets developers write the exact queries they want to use for a given data access operation.
EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead. The first is the translation from LINQ expressions into SQL. These translations are cached, but even so there is overhead in performing them the first time. The second is change tracking on entities (so that efficient update statements can be generated). This behavior can be turned off for specific queries by using the AsNoTracking extension. EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too. In this case, Dapper still outperforms EF Core, but only very slightly. Julie Lerman presents some performance data in her May 2016 MSDN article Dapper, Entity Framework, and Hybrid Apps. Additional performance benchmark data for a variety of data access methods can be found on the Dapper site.
To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:

``` CSharp
// EF Core 
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>>GetCatalogTypes() 
{ return await _context.CatalogTypes.ToListAsync(); } 
// Dapper 
private readonly SqlConnection _conn; public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper() { return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType"); }
```

If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core). This functionality is supported through various syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.


