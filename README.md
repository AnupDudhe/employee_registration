# Employee Management System

It's an application to add and view employee Details.

Referred git repo : https://github.com/shubhamkalsait/devops-fullstack-app.git

## Getting started

Created in 2-tier Architecture in AWS:
1st EC2 instance : for frontend(Ubuntu)
2nd EC2 instance : for backend/sql(Ubuntu)

Created Security Group and add [5432],[8080],[3000] port at inbound rules.

# Login into Frontend Instance:

Update your instance:
```shell
sudo apt update
```
Installing Node.js to run React.js:
```shell
 sudo apt install -y nodejs npm
 sudo npm install -g n  #using nodepackagemanager you have installed a Node.js version manager that allows you to install and manage multiple versions of Node.js on your system.
 sudo n 14.17.0   #This command uses the n package installed in the previous step to install a specific version of Node.js (in this case, version 14.17.0).
 node -v
```
n is a Node.js version manager. It allows you to easily install, manage, and switch between multiple versions of Node.js on your system. With n, you can install different versions of Node.js side by side and quickly switch between them as needed for your projects or development environments.
Clone git repo:
```shell
 git clone https://github.com/shubhamkalsait/devops-fullstack-app.git
```
Go to frontend dir after all this installation and run npm start
```shell
 cd devops-fullstack-app/frontend/
 sudo vim .env #REACT_APP_SERVER_URL=http://localhost:8080/employees --> REACT_APP_SERVER_URL=http://backend_pub_ip:8080/employees
 npm install
 npm start
```

# Login into Backend Instance:

Update your instance:
```shell
sudo apt update
```
Install Postgressql:
```shell
 sudo apt install postgresql postgresql-contrib
```
Login into Postgressql:
```shell
 sudo -u postgres psql
```
After login create DB and User and grant permission to user into Postgressql:
```shell
  CREATE DATABASE db_name; #employees
  CREATE USER user_name WITH PASSWORD 'password'; #test #'1234'
   GRANT ALL PRIVILEGES ON DATABASE db_name TO user_name; #employees #test
   \q
```

Install GO with specific v1.19:
```shell
sudo curl -O https://dl.google.com/go/go1.19.linux-amd64.tar.gz
sudo tar -xvf go1.19.linux-amd64.tar.gz
sudo mv go /usr/local
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH
sudo snap install go --classic
```

Clone git repo:
```shell
 git clone https://github.com/shubhamkalsait/devops-fullstack-app.git
```
Go to backend dir after all this installation and run main.go
```shell
 cd devops-fullstack-app/backend/ 
 DB_HOST=<POSTGRES_HOST> DB_USER=<POSTGRES_USER> DB_PASSWORD=<POSTGRES_PASSWORD> DB_NAME=<POSTGRES_DB_NAME> DB_PORT=<POSTGRES_PORT> ALLOWED_ORIGINS=<ALLOWED_ORGINS_VALUE> go run main.go
 # sudo DB_HOST=localhost DB_USER=test DB_PASSWORD=1234 DB_NAME=employees DB_PORT=5432 ALLOWED_ORIGINS="http://frontend_ip:3000" go run main.go
```
