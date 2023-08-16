# TUTORIAL

## FIND WSL2 IP ADDRESS
```
cat /etc/resolv.conf
wsl hostname -i
172.25.224.1
```

## MYSQL
```
# INSTALL MYSQL CONTAINER WITH docker-compose
MYSQL_USER=user MYSQL_PASSWORD=user MYSQL_ROOT_PASSWORD=@123Test docker-compose up -d

# CONNECTING TO MYSQL
docker exec -it wsl-etc-mysql-1 mysql -p -h 127.0.0.1 -u root
docker exec -it wsl-etc-mysql-1 mysql -p -h 127.0.0.1 -P 3306 --protocol=tcp -u root

# IF mysql_native_password NEEDED
ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY '@123Test';

# COMMAND FOR CLIENT MYSQL WITHOUT DOCKER
mysql -p -h 127.0.0.1 -P 3306 -u root

# MYSQL CONF
/etc/mysql
```

## MSSQL
```
# INSTALL MSSQL CONTAINER WITH docker WITH ACCEPT EULA
docker run -e "ACCEPT_EULA=Y" --name mssql -e "MSSQL_SA_PASSWORD=@123Test" -p 1433:1433 -d mcr.microsoft.com/mssql/server:2022-latest

# CONNECTING TO MSSQL
docker exec -it <container_id|container_name> /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P @123Test
```


# VIEW CONTAINER DETAIL WITH PORT
```
docker container ls -a
```