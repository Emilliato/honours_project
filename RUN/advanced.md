## Running the multiple instances of the same application
To run mutiple instances of the same application (Scaling up the application).

Navigate to the folder with the docker-compose.yml file then run the following commands. The file can be found [here](https://github.com/Emilliato/honours_project/blob/master/RUN/docker-compose.yml)

  ```docker swarm init```

This will initialize the current machine as the manager of the service. Now run the command to deploy the application

  ```docker stack deploy -c docker-compose.yml mars```

**Note:** ``mars`` is the name we are giving to our service and if you are not in the same folder as the compose file then supply the full path. 

We can then use the following commands to monitor the application
 
```docker service ps```
The command above list all running services and also get the ip and port at which our application is running.

We can also use the command:
 
 ```docker service ps mars_web```
 
 to view the status of the service named mars_web. 
 
 ## Deploying the application to a cluster
To do this make sure you have atleast two servers with Docker installed ssh enebled. You can use a virtualbox driver with Docker machine to create machines that we can use as Nodes in your cluster. Make sure you have Docker machine installed. If not check out the installation steps [here](https://docs.docker.com/machine/install-machine/). You can use the following command to create a machine: 

```docker-machine create --driver virtualbox "machine-name"```

After creating the machines you can make one of them the manager by running the following command:

```docker swarm init```

You can then join all other machines by running the following command:

```docker-machine ssh "machine-name" "docker swarm join --token SWMTKN-1-5hc13hv2x2wao8b9bk7x5porbyy53laaw1ov4kscmd9mee3h1c-cnv5ts0o513ljxoa0bu23a90f <master_ip>:2377"```

**NOTE:** The join string is auto generated when you create the master.

After finishing setting up the cluster you can deploy the application to the master using the following command:

``docker stack deploy -c docker-compose.yml mars``

where "mars" is that you are giving your service.

**NOTE** It will take about 10 min for the application to be accessible on the browser using ```localhost:8000``` as the address.

***All done!***

You can use the following commands to monitor the service:

```docker stack ps mars``` #to view the status of the service

```docker node ls``` to view all the nodes in a cluster

