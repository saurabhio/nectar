
### MongoDB Installation
1. Download & Install MongoDB Community Edition
2. Make following folder structure in any drive, say D:,
```
-MongoDB
	-data
		-db
		-log
			-mongo.log
	-mongod.cfg
```
3. In monod.cfg file write this:
```
dbpath=D:\MongoDB\data\db
logpath=D:\MongoDB\data\log\mongo.log
```
4. Start MongoDB service:  ```net start MongoDB```  (listens on port 27017)
5. Install MongoDB: ```mongod --config "D:\MongoDB\mongod.cfg" --install```
6. Now, to run MongoDB client: ```mongo```
7. To stop MongoDB service:  ```net stop MongoDB``` 
8. To remove MongoDB service: ```mongod --remove```

### MongoDB Import & Export
```
mongodump /h abc.def.mongolab.com /port 46719  /u username /p password123  /d dbname /o e:\MongodbBackup
mongodump -d dbname -o e:\MongodbBackup

mongorestore e:\MongodbBackup
mongorestore --db dbname E:\path\to\database\backup

mongoexport --db dbname --collection clname --type=csv --fieldFile fields.txt --out clname.csv
mongoexport --db dbname --collection clname --type=json --fieldFile fields.txt --out clname.json --pretty

bsondump --outFile abc.json abc.bson
mongoimport -d dbname -c clname abc.json
```
