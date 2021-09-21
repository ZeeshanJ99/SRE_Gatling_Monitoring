# Performance Testing

--------------------------------------------------
Installations

## Gatling
add links where downloaded

---------------------------------------------

## Java

download
make environment variable

---------------------------------------------------

## Intellij

download

---------------------------------------

#### setting up testing env
- plugins ctl + alt + s `install scala`
- restart intellij

-------------------------------------------------

## How to monitor

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
-  

---------------------------------------------------------------------------------

## Moving back to the Gatling config screen

- Select Browse and navigate to your `.har` file we created in the previous step
- Add a suitable `class name` for this test
- Press `start`
- This will enable us to convert this `.har` file so we can test it

![image](https://user-images.githubusercontent.com/88186084/134025119-e30d63d9-eb07-47f6-bce9-2a5ac2a5689a.png)


----------------------------------------

## back to terminal

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

## AWS cloud watch

You know when your load balancer and autoscaling groups are working when new instances are spun up to deal with the traffic.


## Application Load Balancer
![image](https://user-images.githubusercontent.com/88186084/134195501-d048d73e-270b-4960-8908-97cac3b35a95.png)

## What we should be monitoring?

Resource monitoring: operates by gathering data on how your servers are running. Resource monitoring tools report on RAM usage, CPU load, and remaining disk space. In architecture with physical servers, information on hardware health—like CPU temperatures and component uptime—can also be helpful to avoid server failure. In cloud-based environments, aggregates of your virtual server system are more useful. 

Network monitoring: Looks at the data coming in and out of your computer network. It captures all incoming requests and outgoing responses across all components such as switches, firewalls, servers, and more. The data collected from network monitoring can be as simple as the total amount of data coming and going or as nuanced as the frequency of particular requests. 

Application performance monitoring: APM solutions collect data on how an overall service is performing. These tools will send their requests to the service and track metrics such as the speed and completeness of the response. The goal is to drive the detection and diagnosis of application performance issues to ensure services perform at expected levels. 

Third-party component monitoring: This involves monitoring the health and availability of third-party components in your architecture. In this era of microservices, your service likely depends on the proper functioning of external services, from cloud hosting to ad servers. Like application performance monitoring, tools can check the status of these services with their requests. 


![MicrosoftTeams-image](https://user-images.githubusercontent.com/88186084/134200831-e1d4f7fe-246f-47c5-a901-41a45778b7c9.png)
