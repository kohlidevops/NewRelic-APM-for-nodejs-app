# To configure the Application Performance Monitoring(APM-Profiling) for sample Nodejs application using NewRelic tool

## Step -1: Configure sample nodejs application

I have launched simple nodejs application in Amazon Linux2023 with the help of Elastic Beanstalk.

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/c706ec4c-6904-4835-ac6d-b2665eb13908)

If i check with Elastic Beanstalk Domain URL

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/7e5369d8-44f9-4fcc-83bb-2d159b3bf1cf)

## Step -2: To create a NewRelic account

You can create a new account using the below link and you can start with free tier.

    https://newrelic.com/signup?via=login

After the creation, you land here. I have already configured and added two more hosts.

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/1ab71851-e857-4fd2-a4d6-afaf85cd3971)

## Step -3: To configure a NewRelic APM

After login, You can see the Add Data in left side panel.

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/1942d5da-6bad-48fb-a2ca-d0c2251016ec)

Add Data -> Click

For my case, My application is based on Nodejs application. So i good to go with nodejs

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/a0b656ab-512a-4135-9df8-42d3d7b52736)

You can play with your requirement here.

Now, you have to choose your instrumentation method - Whether your application is running on host or Docker container. I go with host based

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/97dc8609-9ae0-43b4-b8a0-4d32637d52a4)

Provide meaningful name for your application and save.

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/0a60fec8-586b-4a4b-9089-a3f7f3c8c2cb)

## Step -4: Install the APM Agent

To login your EC2 machine and install the APM agent with the help of below commands.

    npm install newrelic --save

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/1d02574d-113d-47d4-b5f8-05d7db2713e8)

Afer install npm command you can see that newrelic module has been added inside the node_modules.

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/8e895de2-d0e4-43a8-b30e-3d571fa0ff3f)

## Step -5: Install NewRelic Agent

Just copy the newrelic.js from node_modules/newrelic/ to the project root directory.

For my case, the project root directory location is /var/app/current/

    sudo cp /var/app/current/node_modules/newrelic/newrelic.js /var/app/current/

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/fe5befa1-9905-4174-977e-b5367137e373)

Just add these environment varialbles in /var/app/current/newrelic.js

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/c35cf13c-d65a-4d63-99d8-b950ad56dbd1)

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/430a7ded-353b-4aea-bbfc-3e52751300d1)

    cd /var/app/current/
    sudo vi newrelic.js

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/1d3db67d-22a9-490e-a600-fb72f27f0b92)

Place your app name and License key and save it.

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/ef3bf277-13f0-4b11-9cdd-d1ddbf865e88)

Then run the follwing command,

    cd /var/app/current/
    node -r newrelic app.js

Because my main app.js file located in root directory. So you have to run this command where your main js file located.

Next to text your connection from NewRelic

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/0acbe2f8-6d23-4c5d-9daf-d8bc20d023c3)

If its successful then you can see the screen like below.

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/b2de9efd-30e2-4241-b82d-84d0874a3c6d)

Its successfully installed. 

Now you can see your data.

![image](https://github.com/kohlidevops/NewRelic-APM-for-nodejs-app/assets/100069489/f48249f7-45a0-4e69-8d7d-8f558844f905)

Now time to play! You have to do some transaction like any load or performance test on your application with the help Testing team and you can see the transaction traces for Web or Non-Web, Database connection - throughput, query time, SQL traces and so on.

#### If you are not receiving any traces then please restart your application and let check NewRelic.

That's it! I hope there is No Rocket Science to implement this things.
