# Metadata Service 

## local-deployment
1. Build the image ```./run build```
2. ```docker-compose up```
3. Go to Check the Service Section and follow step 2 and 3. Replace `metadata-service-api` with `localhost`

## kubernetes-deployment
1. Make sure minikube is up and running
2. Build the image ```./run build```
3. ```./run deploy```


## Check the service
1. ```kubectl run curl --image appropriate/curl --restart Never -it --command -- /bin/sh```

2. POST to create an entry in the database \
```curl --header "Content-Type: application/json" --request POST --data '{"group":"Thoughtworks India","name":"Mrinal","value":"Gurgaon"}' http://metadata-service-api:8080/metadata```

3. GET an entry posted in step 2 \
```curl http://metadata-service-api:8080/metadata/<id-received-in-post-response>```





# files to chanage for connecting to actual mongodb instance
1) src/main/java/org/boot/services/metadata/InMemoryMongoDB.java
comment @Configuration on line # 8

2) src/main/resources/application.properties
comment out line 24 
uncomment line 25 (remember the name of the mongodb server or change it as you like)



# check mongo database
Use these commands after entering into mongo shell

1.See all your databases: `show dbs` \
2: Select the database: `use your_database_name` \
3: Show the collections: `show collections` \
4: See all the data: `db.collection_name.find()` or `db.collection_name.find().pretty()`