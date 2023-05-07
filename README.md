# project-4

# MEAN STACK DEPLOYMENT TO UBUNTU IN AWS

MEAN Stack is a combination of following components:
MongoDB (Document database) – Stores and allows to retrieve data.
Express (Back-end application framework) – Makes requests to Database for Reads and Writes.
Angular (Front-end application framework) – Handles Client and Server Requests
Node.js (JavaScript runtime environment) – Accepts requests and displays results to end user
Task
In this assignment you are going to implement a simple Book Register web form using MEAN stack.

Step 1: Install NodeJs
Node.js is a JavaScript runtime built on Chrome’s V8 JavaScript engine. Node.js is used in this tutorial to set up the Express routes and AngularJS controllers.

Update ubuntu

sudo apt update
Upgrade ubuntu

sudo apt upgrade
Add certificates

sudo apt -y install curl dirmngr apt-transport-https lsb-release ca-certificates

curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
Install NodeJS

sudo apt install -y nodejs

# # Step 2: Install MongoDB

MongoDB stores data in flexible, JSON-like documents. Fields in a database can vary from document to document and data structure can be changed over time. For our example application, we are adding book records to MongoDB that contain book name, isbn number, author, and number of pages.
mages/WebConsole.gif

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
Install MongoDB

sudo apt install -y mongodb
Start The server

sudo service mongodb start
Verify that the service is up and running  with sudo systemctl status mongodb if everything is fine , then you will see a screenshot like this below

![pro 1](https://user-images.githubusercontent.com/112444993/233506361-7aaf4353-d273-49cb-a8c9-41c7f8af49e4.jpg)

Install npm – Node package manager.

sudo apt install -y npm. the screenshot below shows that npm is install

![pro 2](https://user-images.githubusercontent.com/112444993/233507441-b5e73e1e-7d79-483e-8445-aadb8e884139.jpg)

Install body-parser package

We need ‘body-parser’ package to help us process JSON files passed in requests to the server.

sudo npm install body-parser

![pro 3](https://user-images.githubusercontent.com/112444993/233507756-f78f0574-4680-419e-8f44-a326af6c7c07.jpg)

Create a folder named ‘Books’

mkdir Books && cd Books
In the Books directory, Initialize npm project

npm init and the result is the screenshot below



![pro 4](https://user-images.githubusercontent.com/112444993/233509309-d5908e18-694a-4634-893d-6b1cdc7309ca.jpg)

Add a file to it named server.js and the result is the screenshot below

![pro 5](https://user-images.githubusercontent.com/112444993/233509919-66095ea8-fded-442a-a6bd-58400292123c.jpg)


# INSTALL EXPRESS AND SET UP ROUTES TO THE SERVER

Express is a minimal and flexible Node.js web application framework that provides features for web and mobile applications. We will use Express in to pass book information to and from our MongoDB database.

We also will use Mongoose package which provides a straight-forward, schema-based solution to model your application data. We will use Mongoose to establish a schema for the database to store data of our book register.

sudo npm install express mongoose. and you will you will see result like this.

![pro    (7)     ](https://user-images.githubusercontent.com/112444993/236699427-2dcc3fa2-62eb-4e09-871a-767fe9989770.jpg)

In ‘Books’ folder, create a folder named apps

mkdir apps && cd apps
Create a file named routes.js

vi routes.js
In the ‘apps’ folder, create a folder named models

mkdir models && cd models
Create a file named book.js

vi book.js

Step 4 – Access the routes with AngularJS
AngularJS provides a web framework for creating dynamic views in your web applications. In this tutorial, we use AngularJS to connect our web page with Express and perform actions on our book register.

Change the directory back to ‘Books’

cd ../..
Create a folder named public

mkdir public && cd public
Add a file named script.js

vi script.js

In public folder, create a file named index.html;

vi index.html

Change the directory back up to Books

cd ..
Start the server by running this command:

node server.js
The server is now up and running, we can connect it via port 3300. You can launch a separate Putty or SSH console to test what curl command returns locally.

curl -s http://localhost:3300
It shall return an HTML page, it is hardly readable in the CLI, but we can also try and access it from the Internet.

For this – you need to open TCP port 3300 in your AWS Web Console for your EC2 Instance.

You are supposed to know how to do it, if you have forgotten – refer to Project 1 (Step 1 — Installing Apache and Updating the Firewall)

Now you can access our Book Register web application from the Internet with a browser using Public IP address or Public DNS name.

Quick reminder how to get your server’s Public IP and public DNS name:

You can find it in your AWS web console in EC2 details
Run curl -s http://169.254.169.254/latest/meta-data/public-ipv4 for Public IP address or curl -s http://169.254.169.254/latest/meta-data/public-hostname for Public DNS name.
This is how your Web Book Register Application will look like in browser:


![pro (10)](https://user-images.githubusercontent.com/112444993/236700931-29a3ce50-cb9f-4ef6-a24a-2c7594ad8454.jpg)

