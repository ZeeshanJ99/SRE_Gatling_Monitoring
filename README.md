# Performance Testing

![image](https://user-images.githubusercontent.com/88186084/134348100-56a4f053-25d2-4b65-84f6-547550c81dd7.png)

--------------------------------------------------
# Installations
-----------------------------------

## Gatling
- https://gatling.io/get-started/
- Download normal one (not enterprise)

---------------------------------------------

## Java
- https://devwithus.com/install-java-windows-10/
- Download the installer
- make environment variable

---------------------------------------------------

## Intellij
- https://www.jetbrains.com/idea/download/#section=windows
- Download community version

#### setting up testing env on intellij
- plugins ctl + alt + s `install scala`
- restart intellij

---------------------------------------

## Maven Installation

- https://maven.apache.org/download.cgi 
- Download the zip file and move it to your program files
- Go to Environment variables and make a new user variable named path with the value as the path of the Maven file with `\bin` at the end
- create a new system environment variable named `MAVEN_HOME` and provide the value as the path of the Maven file
- Use `mvn --version` to check whether it has installed properly on your terminal

-----------------------------------------

## What we should be monitoring?

**Resource monitoring**: operates by gathering data on how your servers are running. Resource monitoring tools report on RAM usage, CPU load, and remaining disk space. In architecture with physical servers, information on hardware health—like CPU temperatures and component uptime—can also be helpful to avoid server failure. In cloud-based environments, aggregates of your virtual server system are more useful. 

**Network monitoring**: Looks at the data coming in and out of your computer network. It captures all incoming requests and outgoing responses across all components such as switches, firewalls, servers, and more. The data collected from network monitoring can be as simple as the total amount of data coming and going or as nuanced as the frequency of particular requests. 

**Application performance monitoring**: APM solutions collect data on how an overall service is performing. These tools will send their requests to the service and track metrics such as the speed and completeness of the response. The goal is to drive the detection and diagnosis of application performance issues to ensure services perform at expected levels. 

**Third-party component monitoring**: This involves monitoring the health and availability of third-party components in your architecture. In this era of microservices, your service likely depends on the proper functioning of external services, from cloud hosting to ad servers. Like application performance monitoring, tools can check the status of these services with their requests. 

---------------------------------------------------------

## The 4 Common performance tests

There are four common types of performance tests designed to assess applications:

- **Load Tests**: Measure performance as a workload increases to expected production levels. The goal is to ensure that any updates to an application continue to meet minimum performance standards.

- **Stress Tests**: Measure performance outside of typical production levels to measure when and how it fails. The goal is to identify the breaking points of an application and potentially fix bottlenecks.  

- **Spike Tests**: Measure performance when a workload suddenly and substantially increases beyond typical production levels. The goal is to see how an application would perform if traffic suddenly spiked in production.

- **Soak Tests**: involves testing a system with a typical production load, over a continuous availability period, to validate system behavior under production use. 

--------------------------------------------

## How to monitor with Har converter

- Open the gatling highcharts bundle in intellij
- in the terminal `cd bin` 
- `ls` should show these files
![image](https://user-images.githubusercontent.com/88186084/134022189-378b97cf-f4ce-4858-9963-3ceca91e47d2.png)

use the command `./recorder.bat` in the terminal to bring up this window

![image](https://user-images.githubusercontent.com/88186084/134022662-0b72c9b7-2d7e-4bbc-b0b6-35aa99eca827.png)

We will now change the recorder mode to HAR converter which shall change the page as such. Note that the Gatling configuration page is not very user friendly so you may need to open it in a full screen format to see everything on the page.

![image](https://user-images.githubusercontent.com/88186084/134022878-ef14e8af-5252-4045-8d9a-59dca436c298.png)

------------------------------------------------------------------------------------

## Converting the .har file
The HTTP Archive format, or HAR, is a JSON-formatted archive file format for logging of a web browser's interaction with a site. The common extension for these files is .har

Navigate to a webpage of your choice on Google Chrome. In this case we will be using Jenkins. On any space on the screen, right-click and select inspect.

![image](https://user-images.githubusercontent.com/88186084/134023462-2fc092e9-8797-4a81-883c-3d75424b5942.png)


This will bring up this section
![image](https://user-images.githubusercontent.com/88186084/134024387-cf91c6c9-062c-4100-bdcc-107dd69fbd41.png)

Use the `clear` button to clear any history and like the image above make sure that `preserve log` is ticked

- On the Jenkins page we will now login in order for a recording to take place
- Once logged in use the `export HAR` which will download a `.har` file to your local machine. Save this in a memorable place.


---------------------------------------------------------------------------------

## Moving back to the Gatling config screen

- Select Browse and navigate to your `.har` file we created in the previous step
- Add a suitable `class name` for this test
- Press `start`
- This will enable us to convert this `.har` file so we can test it

![image](https://user-images.githubusercontent.com/88186084/134025119-e30d63d9-eb07-47f6-bce9-2a5ac2a5689a.png)


----------------------------------------

## back to the terminal

- In the terminal use the command `./gatling.bat` this may take some time but will show the different simulations that are available including our own that we just created
- Type the number where our simulation is present, in this case `0` and press enter
- A prompt `select run description` will popup, in this we shall use a suitable name and again press enter
- Now the testing will begin!

![image](https://user-images.githubusercontent.com/88186084/134025773-78e39b21-a252-4015-941b-62d702abec2d.png)


---------------------------------------------------------------

## Gatling stats
Once testing is completed copy and paste the path it provides onto google chrome

![image](https://user-images.githubusercontent.com/88186084/134026296-b46bb941-2dc3-4c17-b792-c0c5b8ff244e.png)

This will bring us to the Gatling Stats homepage. Here we can see lots of information including requests that have passed and failed etc.

![image](https://user-images.githubusercontent.com/88186084/134026523-ad8e3cfc-f1ae-4c19-874b-33a6425ddde9.png)


-------------------------------------------------------------------------------

## Editing requests

Navigate to this section

![image](https://user-images.githubusercontent.com/88186084/134032638-a558a981-8e70-4af2-953b-b108059891b6.png)

Scroll to bottom of page, this number is the number of requests that will occur when you test 

![image](https://user-images.githubusercontent.com/88186084/134032886-78de4750-da59-4059-8a3f-d565c55d1410.png)

Set this to a suitable number


-----------------------------------------------------------------------------------------

## What is an Application Load Balancer (ALB)?
The Application Load Balancer is a feature of Elastic Load Balancing that allows a developer to configure and route incoming end-user traffic to applications based in the AWS public cloud. It can address complex load-balancing needs by managing traffic at the application level

![image](https://user-images.githubusercontent.com/88186084/134195501-d048d73e-270b-4960-8908-97cac3b35a95.png)

------------------------------------------------

## What is Scaling in and Scaling out and what differences do they have?

Scaling out, or horizontal scaling, contrasts to scaling out, or vertical scaling. As your cloud workload changes it may be necessary to increase infrastructure to support increasing load or it may make sense to decrease infrastructure when demand is low. Scaling out is adding more equivalently functional components in parallel to spread out a load. **This would be going from two load-balanced web server instances to three instances. Scaling up, in contrast, is making a component larger or faster to handle a greater load.  This would be moving your application to a virtual server (VM) with 2 CPU to one with 3 CPUs.**  For completeness, scaling down refers to decreasing your system resources, regardless of whether you were using the up or out approach.


![image](https://user-images.githubusercontent.com/88186084/134346129-dc90ab8f-94de-425c-b7cf-a65b58aa8201.png)


---------------------------------------------------------------------------------------------

## AWS cloud watch

![image](https://user-images.githubusercontent.com/88186084/134348414-dc96a9ff-a031-48fd-b313-3d8fd56932fb.png)


You know when your load balancer and autoscaling groups are working when new instances are spun up to deal with the traffic.

Use this link to learn how to set it it up and automate it in terraform! - https://github.com/ZeeshanJ99/SRE_terraform/blob/main/README.md

---------------------------------------------------------------------------------

### Simple Notification Service (SNS)

- Navigate to the `SNS` dashboard and select `Topics`
- Select `Create topic`
- Select `standard` as the type
- Name it appropriately and add `tags`
- Once created you can click on your topic and `create a subscription`
- select `email` as the protocol
- Place your email in the `endpoint` box
- This will send an email to the email you specified asking for you to confirm it.
- Once confirmed your set-up is complete and you can add this SNS to an alarm

-----------------------------------------------

### Creating an Alarm on Cloudwatch

- Navigate to CloudWatch
- Click `Create Alarm`
- Press `Select Metric` followed by what you would like the alarm to trigger, for example `CPUUtilization`
- To get to a metric click on  `EC2 > By Auto Scaling Group`, find your ASG and tick `CPUUtilization`
- Click `Select Metric` This will bring you to a page where you specify the Metric and Conditions

- Change the `Period` to `1` minute
- Condition as `Static` , `Less than < threshold` and define the value as a suitable number e.g.`20`
- Click `Next`
 
- At this stage you can add your `SNS Topic` that we created earlier
- And `add Auto Scaling action`
- Select the `In alarm` and `Resource type as EC2 Auto Scaling group` and select your group from the dropdown menu
- On `Take the following action` select what will happen once the alarm is triggered, e.g. `scale down (remove 1 instance)`
- Click `Next` Add your alarm `name` and a `description`
- Now you can `Create` your alarm 

-----------------------------------------------------------------------------------------------

Create a Diagram for each service and the entire process of making your App highly available and scalable 

E.g. ASG - how is it connected to load balancer - how connected to the Internet Gateway etc.



