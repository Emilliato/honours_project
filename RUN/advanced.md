## Running the multiple instances of the same application
To run mutiple instances of the same application (Scaling up the application).

Navigate to the folder with the docker-compose.yml file then run the following commands. The file can be found [here](https://github.com/Emilliato/honours_project/blob/master/RUN/docker-compose.yml)

  ```docker swarm init```

This will initialize the current machine as the manager of the service. Now run the command to deploy the application

  ```docker stack deploy -c docker-compose.yml mars```
  # mars is the name we are giving to our service
We can use the following commands to monitor the application
 docker service ps
 # list all running services
 docker service ps mars_web
2.
