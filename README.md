# ICSA2020_Submission90
This is the repository of the ICSA submission 90. The implementation details and result replication for M-View4Adapt framework are presensented below:


## Experiment Setup and System Configurations

The system consists of sensors deployed on the edge, lightweight computation distributed to a Fog and microservices deployed on the cloud. 

#### Microservice deployment Configurations

The microservices were deployed on two Google Cloud instances with different geographical zones.The first one was run on a N1-Standard-4 CPU Intel Haswell Processor comprising 4 vCPU and 16 GB RAM with US-Central-1a as the geographical zone and Ubuntu 20.04 LTS. The second one ran on a N2-Standard-4 Intel Skylake processor comprising 2 vCPU and 8 GB RAM with US-Central-1c as the geographical zone and Ubuntu 18.04 LTS.

#### Fog and IoT deployment Configurations

To emulate the edge layer setup, one desktop machine with 8 GB RAM and Intel 3rd Generation i5 (2.6 GHz quad core) with Ubuntu 16.04 LTS was used to run the CupCarbon simulation. Further, a Macbook pro with 16GB RAM and 8th Generation Intel i7 1.7 GHz (Quad Core) was used to deploy the Fog layer. 


## XYZ Case Study Application Architecture

![XYZ base application architecture](XYZ_Application.png)


## M-View4Adapt Techstack






#### Installation Requirements

1. Docker - https://docs.docker.com/get-docker/
2. Elasticsearch - https://www.elastic.co/downloads/elasticsearch?latest
3. MySQL - https://dev.mysql.com/doc/mysql-installation-excerpt/8.0/en/windows-install-archive.html
4. Python 3.7+ - https://www.python.org/downloads/
5. Apache Kafka - https://kafka.apache.org/quickstart


## Python Package requirements

1. asyncio
2. kafka-python
3. elasticsearch
4. mysql-connector-python
5. matplotlib
6. numpy
7. pandas



## Running Microservices as Docker Containers:

Each folder with "_service_" in the name essentially is a microservice. To run the service move into the directory using a _cd_ command and execute the following:


```shell
sudo docker build  -t image_name .
sudo docker run -e PORT_NUM=port ES_HOST=localhost -it --name image -p port:port image_name
```

The ES_HOST in the previous statement is an argument to specify the IP of the elasticsearch instance and port denotes the port where the webservice listens to. To run multiple instances of the same microservices, simply keep running them in different ports by changing the values for port argument

## User Goal Request Simulation

All the user related script can be found inside the folder *user_simulation* This is used for simulating the user goal requests
The goals can be found in the file *main_user_goal_file.txt*

1. *async_test.py* can be run to simulate the user requests to XYZ application that uses dynamic goals. 
2. *static_application_simulator.py* can be run to simulate user requests to XYZ application with predefind static flow

**Note:** In both the above scripts, update the "localhost" to ip address of the corresponding servers where microservices are hosted

## Edge and Fog Layer

The edge layer has been simulated using CupCarbon Simulator. All edge related implementation can be found in the folder IoT_Simulation_Adaptation. Open the folder and follow the below steps:

1. CupCarbon-master_4.0 contains the modified source code of cupcarbon. The application can be started by running cupcarbon.java. Inside the source folder, go to  senscript_functions/Functions.java, add the path for "config.txt" in line 209
2. Run the CupCarbon from the modified source code (First import the CupCarbon-Master_4.0 as an eclipse project, Same can be done if you are uisng IntelliJ IDE)
3. XYZ_Case contains the cupCarbon project of the case study mentioned in the paper. It can be opened by opening the XYZ.cup filefrom the open project option available in the cupCarbon UI. Further details can be found in www.cupcarbon.com The natevents folder contains the sensor datasets used which was generated based on real observations of the case study which followed a poisson distribution.
4. Open the XYZ_Case project from the open project option in cupCarbon UI
5. Set the simulation parameters in cupCabron to five hours (18000 s), mark the result field for 60s and run the Simulation
6. Immidiately run the programs CupCarbon_Energy_Streamer.py and adaptation_handler.py

## Cloud Layer






