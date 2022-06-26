# MongoDB Cheet-Sheet

***Login to Database***

`mongo -u USER -p --authenticationDatabase admin`

`mongo -u USER -p --authenticationDatabase DATABASE`

***Show all databases***

`show dbs`

***Create a database***

`use testdb`

***Add a collection***

`db.createCollection("user")`

***Show all collections in a database***

`show collections`

`show tables`

***Insert a record in collection***

`db.user.insert({"name": "Jalal Zivari", "location": "Iran", "username": "jzd"})`

***Display list of records of a collection***

`db.user.find()`

`db.user.find().pretty()`

***Display a list of records matching with value (s) of specific fields***

`db.user.find({"username": "eajitesh"})`

`db.user.find({"username": "eajitesh", "location": "hyderabad"})`

***Drop the collection***

`db.user.drop()`

***Drop a database***

`use testdb`

`db.dropDatabase()`

***Create users in the database***

`db.createUser({"user": "test", "pwd": "test", "roles": ["readWrite", "dbAdmin"]})`

***Show users*** 

`show users`

***Create user***

`use my_db;`

`db.createUser({user : "MY_USER", pwd : "123456" , roles: [ { role: "readWrite", db: "MY_DB" } , {role: "userAdmin" , db: "MY_DB"} ] } );`

`db.createUser( { user: "monitoring",pwd: "Pass1234",roles: [  { role: "clusterMonitor", db: "admin" }]})`

***reset user password***

`use products`

`db.changeUserPassword("MY_USER", passwordPrompt())`

Or

`use products`

`db.changeUserPassword("MY_USER", "123456")`


***Check Replication***

`rs.conf()`

`rs.status()`


`rs.printSlaveReplicationInfo()`

`rs.printReplicationInfo()`

***Dump all databases***

`mongodump -u test  --out /opt/all`

***Restore all Databases***

`mongorestore  -u test  --drop /opt/all`

***Dump specific collection*** 

`mongodump -u test --authenticationDatabase admin  --db exampleDB2 --collection exampleCollection --out /opt/exampleCollection`

***Restore specific collection*** 

`mongorestore -u test --authenticationDatabase admin --db exampleDB2 --collection exampleCollection --drop /opt/exampleCollection/exampleDB2/exampleCollection.bson`

***Dump specific database***

`mongodump -u test --authenticationDatabase admin  --db exampleDB2 --out /opt/exampleDB2`

***Restore specific database***

`mongorestore -u test --authenticationDatabase admin --db exampleDB2 --drop /opt/exampleDB2/exampleDB2/exampleCollection.bson`

***Import scripts***

`mongoimport --db test --collection inventory \`

`--authenticationDatabase admin --username <USER> --password <PASSWORD> \`

  `--drop --file ~/Downloads/inventory.crud.json`

***show current connections***
 
 `db.serverStatus().connections`
