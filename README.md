### RESTful-Web-Service-Implementation-Docker

Developed RESTful web service called ‘Customer Management System’ leveraging Java Spring Boot Application and MySQL database to store customer-orders details. Web service exposes 4 REST APIs:

1.	getAllCustomers() 
    
        /customers

2.	getCustomerById()

        /customers/{custId}

3.	getOrdersByCustId()

        /customers/{custId}/orders

4.	getOrdersByOrderId()

        /customers/{custId}/orders/{orderId}

These endpoints are consumed by Angular7 client application.

MySQL database contains data about customers and their orders:

![image](https://user-images.githubusercontent.com/94254884/146081368-fec1b530-ad49-4e53-a915-f12d6b9a6814.png)

![image](https://user-images.githubusercontent.com/94254884/146081427-f59a8baf-2549-4305-933f-8e1302db476f.png)


Steps to build and run applications on docker:

Note: You must have docker installed on your PC to successfully run the project. See below link to install docker.

    https://docs.docker.com/get-docker/

Command to create network bridge: 	

    docker network create customer-mysql

Download docker mysql image from below link:

    https://hub.docker.com/_/mysql
    
Command to create mysql container:

    docker container run --name mysqldb --network customer-mysql -e MYSQL_ROOT_PASSWORD=19961226 -e MYSQL_DATABASE=bootdb -d mysql:8

Command to enter mysql bash and enter mysql credentials:

    docker container exec -it container_initials bash
    mysql -uroot -p19961226

Note: Application automatically creates the tables, so you just need to insert records in the tables. If application does not create tables, you need to create tables: customer and orders (refer above table schema) and insert records in tables. (DB scripts are attached within this repository)

## To setup the web service application:

Download service application from git. Unzip and open terminal. 

Change directory to service application location using cd command.

Run below command to create docker image for spring boot application (web service):

    docker image build -t customer-jdbc .

Command to run application using docker containers on port 8080:

    docker container run --network customer-mysql --name customer-jdbc-container -p 8080:8080 -d customer-jdbc
    
## To setup the client application: 

Open another terminal window to run client application.

Change directory to the location of client application using cd command.

Now run the below command:  

    npm install
 
To run client application, execute below command: 

    ng serve

## To see the output, copy below URL in your web browser:

    http://localhost:4200












