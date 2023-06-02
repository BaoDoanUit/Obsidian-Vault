---
up: [[What Software Architecture 101]]
---
### Multitenancy explained in simple words

![[SoftwareArchitect-1.webp]]

### Use Cases
1. SaaS
2. PaaS
3. IaaS
4. For all other applications where multiple clients use the same stack of algorithms. The main functionality is either the same or modular, and it can be tailored to any of the client's needs
### Key differences between single-tenant and multi-tenant models

#### Isolation
single-tenant: A separate app, infrastructure, and database for each tenant
multi-tenant: A single app and shared resources for all tenants
#### Security
single-tenant: Full isolation for a potential more secure app
multi-tenant: Tenants may share the same database, so additional security steps should be taken by the vendor
#### Scalability
