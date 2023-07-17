# MySQL Docker Setup Guide
This guide provides a step-by-step process on how to set up a MySQL server inside a Docker container.

## Prerequisites
- A Linux operating system with Docker installed
- Sudo or root access privileges

## Steps
### 1) Prepare the environment
Launch your Linux OS terminal and install Docker if it's not already installed. Use the following commands to install Docker and set it up to start on the system boot:

```
sudo su -
yum install docker -y
systemctl start docker 
systemctl enable docker 
```
### 2) Pull the MySQL Docker image

Now that Docker is installed, pull the latest version of MySQL Docker image from the Docker Hub using the following command:

```
docker pull mysql
```

### 3) Run MySQL Docker container

To run the MySQL Docker container in detached mode, use the command below. This command includes initial setup such as root password, database name, username, and password. Make sure to replace the variables like toor, mydb, user, etc. with your desired values.

```
docker run -dit --name mydb -e \
MYSQL_ROOT_PASSWORD=toor -e \
MYSQL_DATABASE=mydb -e \
MYSQL_USER=user -e \
MYSQL_PASSWORD=toor \
mysql
```

### 4) Access MySQL Docker Container

To access the MySQL Docker container and execute a bash shell, use the following command:
```
docker exec -it mydb bash
```
### 5) Log in to your MySQL server

You can now log in to your MySQL server using the credentials set in step 3. Replace 'user' and 'toor' with your own username and password:

```
mysql -u user -ptoor
```

### 6) Use the MySQL server

Once logged into MySQL, you can use SQL to interact with your database. For example, use the following command to show all databases:

```
SHOW DATABASES;
```

Congratulations! You have now successfully set up a MySQL instance inside Docker. Ready to start querying? Happy coding!