# Zia-Mart
Kafka Event Driven with Kong Microservices Project using Fast API

# Islamabad Help Desk Session 01
https://www.youtube.com/watch?v=5dGNFpDTH7U

# Cloning Repository
(https://github.com/panaverse/learn-generative-ai)

Make a Directory
Inside the Directory, Enter VS Code, and in Powershell 

Run this command

```
git clone https://github.com/panaverse/learn-generative-ai.git
```
As we need not to do Pull, So, goto Cloned Folder, and delete ``` .git ``` file

Now, in you cloned folder, Go to

* Step 05_microservices_all_in_one_platform, then go to
* Step 15_event_driven and finally, to
* 02_kafka_messaging

Now Open you VS Code

Open ```compose``` file

* First Run DOCKER DESKTOP, then(Docker must be installed in the system)
* Run ```docker compose up```

Once process is completed,check Your 
*Doker Desk top for Containers
-Postgres
-broker
-api 1
-api 2
-kafka ui

# Creating First Product Microservice

There are two ways to do that, either

* Create a Folder, or
* Run ```poetry new product_service```
* Create Docker File of Product_Service as a sibling of ```toml``` file (One way to copy other service's Docker file and make changes accordingly)
* Create ```main.py``` in Product_Service Folder
* Now add Fast API by running command ```poetry add fastapi```. It must in Parent Directory of Product Microservice. Otherwise there will be Error.

# Islamabad Help Desk Session 02
https://youtu.be/QkD7gI7bmHU
