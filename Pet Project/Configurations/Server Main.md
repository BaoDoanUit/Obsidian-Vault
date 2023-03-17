Tunnel
- [List tunnel services](https://github.com/anderspitman/awesome-tunneling)
Environment
- Dotnet: 
     - [Install Scripted](https://learn.microsoft.com/en-us/dotnet/core/install/linux)
- PostgreSQL
     - [Install PostgreSQL for linux-mint](https://www.tecmint.com/install-postgresql-with-pgadmin4-on-linux-mint/)
     - [Fix Install python lib](https://stackoverflow.com/questions/75137717/eventlet-dns-python-attribute-error-module-dns-rdtypes-has-no-attribute-any)
     - [Set password for postgres user](https://stackoverflow.com/questions/12720967/how-can-i-change-a-postgresql-user-password) 
          - ```psql
          sudo -u postgres psql -c "ALTER USER postgres PASSWORD 'Qn0982190003';"
     - [Configuration remote postgreSQL](https://blog.logrocket.com/setting-up-a-remote-postgres-database-server-on-ubuntu-18-04/)
     - [Configuration port](https://www.project-open.com/en/howto-postgresql-port-secure-remote-access)
- OpenSSH
     - [Install](https://linuxhint.com/enable-ssh-linux-mint/)


Issues:
https://superuser.com/questions/1670429/create-a-https-tunnel-to-avoid-network-hard-limitations

https://linuxconfig.org/how-to-install-and-configure-dropbear-on-linux
https://github.com/localtunnel/localtunnel/issues/120


 curl -O https://pagekite.net/pk/pagekite.py  
 python pagekite.py 42  baodoan.pagekite.me


[Issues SSL](https://stackoverflow.com/questions/52540899/disabling-certificate-check-in-grpc-tls)



Machine 1 (AnyDesk hongphucserver@ad) 192.168.1.8
- ngrok tcp 5432 (Postgresql) 
- localtunnel 3000 (GateWayAPI)
- localhost 3004 (IdentifyServer)
- Message Queue

Machine 2 (AnyDesk hongphuc-f789jti@ad) 192.168.1.4
- Batch Process
     - Run repeatedly after 15 minutes
- Consumer
- Producer


Cloud
- (API) https://app.cyclic.sh/#/app/baodoanuit-ecommerce/builds

