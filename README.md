# Zia-Mart
Kafka Event Driven with Kong Microservices Project using Fast API

# Islamabad Help Desk Session 01 
### (KAFKA MESSAGING STEP)
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
* Now add Fast API by running command ```poetry add fastapi```. It must in Parent Directory of Product Microservice. Otherwise there will be Error. So for that, run ```cd procut_service``` and run  ```poetry addfastapi``` Now ```toml``` file will show ```fast api```
* List Product_Service in ```Yaml compose``` file
* Do changes in Yaml file for new Product_Service
* Then we launch its container

BUILDING CONTAINER IN main.py
```
from fastapi import FastAPI
app = FastAPI ( )

@app.get ( “/”)
async def root ( ):
	return {“message”: “Product Service”}
```
On Power Shell, Run
```

docker compose up -- build

```
To verify,whether Docker Compose in valid, then go to directory 
```
cd .
```
and RUN in power Shell
```
docker compose config
```

## We use -- build to re-create the container up,because we have changed by add a new service
** Even you have cloned a repository, better use command (Best Practice)
```
docker compose up --build
```
### If you modify your compose file without changing the code, avoid using the --build command.
### We can also achieve this using Dev Containers since we have mapped volumes.
**ERROR:** Port is already allocated </span>

[ ] One solution is to change the Port Number of New Service 
Afterward, we have to use 
```
docker compose up
```
Not
```
docker compose --build
```
As changes are made in compose file, not in the code

### _Containers, such as various machines or laptops, resemble distinct entities within an isolated LINUX environment, all sharing the same host. Each container is capable of operating on port 8000. These laptops or machines coexist within the same network. Currently, our host serves as the Operating System responsible for port mapping._

### Open pg-admin and connecting New Microservice to Database
*First step is to CONFIG the Postgress db server

# Islamabad Help Desk Session 02
https://youtu.be/QkD7gI7bmHU

### _in tradional style we use API to perform CRUD, Whereas in Event Drive, we use KAFKA to do same._

![image](https://github.com/zulfiqaralimir/Zia-Mart/assets/68346772/4510e0de-a2a9-48cd-a6ef-588ee322cca5)

* We will use PROTOBUF to serialize the data. It is speedy as compared to JSON serialized data format.
* Creating FAST API to to create PRODUCERS and CONSUMERS
* Product Service will act as Producer
* The toml file look like

* ![image](https://github.com/zulfiqaralimir/Zia-Mart/assets/68346772/bc34763b-a77a-46d6-937e-a7f9d76c6095)

* **aiokafka** will help to conect python code to broker.
* protobuf is here to create buffers that is binary data that is used to serialized the data.
* In ```main.py``` we have to create AIOKafkaAdminClient.it connect Product Service to Broker port
* As there is depend on between kafka broker and product service, there may be lag between that can cause disconnection. While loop code will be utilized to restart after certain time to handle the situation. (10 seconds)
* Now Topic will be created in the name of Product using ```lifespane```.
* First Topic is created and then messages comes into that topic. Producer is attached with that topic and this producer creates topics whereas Consumer consumes those messages.
* Consumer will later perform action on those received messages like putting in db etc.
* AIO Kafka will be used to create Producer (Using Dependency Injection)
* Code will performed in DEV CONTAINER otherwise we have to update again and again.
* *If you use JSON then we have to us 'b' as prefix to let know compiler to convert the code in serialized form, whereas in PROTOBUF, it is not the case,as PROTOBUF does it itself, skipping this step.*
* ### What is PROTOBUF
* ![image](https://github.com/zulfiqaralimir/Zia-Mart/assets/68346772/7ff7c087-68ec-44f2-96b0-c092a4ff76e4)

* In PROTOBUF we create a Schema like Custom data type
* In PROTOBU, OperationType, let consumer know what CRUD Operation has to be performed.
* PROTOBUF, can not be imported into main.py, as it not python code. So a compiler is used to convert it in python style
* We will use GitHub repo to install PROTOBUF Compiler.
* (https://github.com/protocolbuffers/protobuf)

* Go to GitHub release page. In ASSETS, intall desired one.
* Copy the Bin folder path and past it into environmental variable
* RUN on Command
* ```poetry add protobuf```
* ```protoc --version```
* Now We can compile PROTOBUF file into python code.
* We to be in product_service,for that
* ```cd product_service```
* ```ls``` it will show, PROTO file
* Now Run
* ```protoc --python_out=../product.proto```

* Now in ```main.py```import protobuff
* Here we will initialize Product Class
* We will have ```product_pb2.py``` file (protobuf). This file has schema.
### Consumer
* 

