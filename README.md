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



## Running Microservices as Docker Containers:

Each folder with "_service_" in the name essentially is a microservice. To run the service move into the directory using a _cd_ command and execute the following:


```shell
sudo docker build  -t image_name .
sudo docker run -e PORT_NUM=port ES_HOST=localhost -it --name image -p port:port image_name
```

The ES_HOST in the previous statement is an argument to specify the IP of the elasticsearch instance and port denotes the port where the webservice listens to. To run multiple instances of the same microservices, simply keep running them in different ports by changing the values for port argument

## Edge Layer



