1. Mutiple instances of the same application (Scaling up the application).
Navigate to the folder with the docker-compose.yml file then run the following commands
  docker swarm init
  #Initialize the current machine as the manager of the service
  docker stack deploy -c docker-compose.yml mars
  # mars is the name we are giving to our service
We can use the following commands to monitor the application
 docker service ps
 # list all running services
 docker service ps mars_web
2.
