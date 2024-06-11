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

_Containers, such as various machines or laptops, resemble distinct entities within an isolated LINUX environment, all sharing the same host. Each container is capable of operating on port 8000. These laptops or machines coexist within the same network. Currently, our host serves as the Operating System responsible for port mapping._

# Islamabad Help Desk Session 02
https://youtu.be/QkD7gI7bmHU
