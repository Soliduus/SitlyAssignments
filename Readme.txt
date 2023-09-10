Running Lighthouse Audit Job with Jenkins in Docker

This guide will walk you through the steps to run a Lighthouse audit job using Jenkins within a Docker container. 
The Lighthouse audit will be performed on a specified URL to assess web performance, accessibility, and best practices.

The Jenkins setup including the job data has been packaged into a docker .tar file. 

As a prerequisite, docker must be installed. I recommend installing Docker Desktop to also include a GUI for docker actions;
The following guide includes instructions on how to install docker desktop:
https://docs.docker.com/desktop/install/windows-install/

Note that this jenkins is packaged into a linux image. 
This means that you also need to install WSL 2 (Windows Subsystem for Linux) first.  
The following guide includes instructions on how to install WSL:
https://www.omgubuntu.co.uk/how-to-install-wsl2-on-windows-10

When you start Docker Desktop on Windows, make sure to run it in Linux Container mode.
To do this, go to the bottom right of your screen and rightclick the Docker Desktop icon and select *Switch to linux containers*
If the option is not present, it means you are already in this mode.

When you are ready to run the docker image, run the following command in a command prompt to unpackage:
docker load -i <path to image tar file>

The image should now be loaded into docker, to verify, run
docker images

To run the image, run the following command:
docker run -p 8080:8080 -p 50000:50000 -v /var/run/dbus/system_bus_socket:/var/run/dbus/system_bus_socket lighthousejenkins

You can now enter the Jenkins UI by visiting http://localhost:8080/ on your host machine browser

Log into jenkins using:
Username: 	Idan
Password:	HireReinierNow!

The job is now runnable in Jenkins.
You can hover over the 'LightHouse_Pipeline' job, and click on the arrow to view the drop down;
There, you can select 'Build with Parameters' and input a URL to run lighthouse on. By default, https://www.google.com is filled out.

When the job is finished, refresh the view to see the 'Lighthouse Report' tab show up on the lefthand side.