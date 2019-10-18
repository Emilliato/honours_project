# **MARS WEB**
Repackaged version of the MARS bioinformatics project developed by a Bioinformatics PhD. student.

## **Running the service**

To run the service, first make sure that you have Docker installed on your machine. If you have not done so and you are running ubuntu follow the guide [here](https://github.com/Emilliato/honours_project/blob/master/LabReportsSub/installation.txt)  or follow the installation guide from Docker [here](https://docs.docker.com/install/linux/docker-ce/ubuntu/).

There are two ways of running this application:  

### **Simple way**
This can be used if you want to run a single instance of your application. To do that you can run the command:

&nbsp;&nbsp;&nbsp;&nbsp;**$**``` docker run -p 8000:8000 -d -t g19m2952/mars_web:sqlite_1.00 ```

**NOTE:** This will run the container in the background and exposes maps port ```8000``` of the container to port ```8000``` on the host. So make sure that port ```8000``` is not allocated to any other service on your server. 

The application can now be accessed on the browser using ```localhost:8000```

