# Apache-NiFi

Apache NiFi is a powerful, easy to use and reliable system to process and distribute data
between disparate systems. It is based on Niagara Files technology developed by NSA and
then after 8 years donated to Apache Software foundation. It is distributed under Apache
License Version 2.0, January 2004. The latest version for Apache NiFi is 1.7.1.
Apache NiFi is a real time data ingestion platform, which can transfer and manage data
transfer between different sources and destination systems. It supports a wide variety of
data formats like logs, geo location data, social feeds, etc. It also supports many protocols
like SFTP, HDFS, and KAFKA, etc. This support to wide variety of data sources and
protocols making this platform popular in many IT organizations.

# Apache NiFi-General Features

● Apache NiFi provides a web-based user interface, which provides seamless
experience between design, control, feedback, and monitoring.

● It is highly configurable. This helps users with guaranteed delivery, low latency,
high throughput, dynamic prioritization, back pressure and modify flows on
runtime.

● It also provides data provenance module to track and monitor data from the start
to the end of the flow.

● Developers can create their own custom processors and reporting tasks according
to their needs.

● NiFi also provides support to secure protocols like SSL, HTTPS, SSH and other
encryptions.

● It also supports user and role management and also can be configured with LDAP
for authorization.

# Apache NiFi -Key Concepts

● Process Group: It is a group of NiFi flows, which helps a user to manage and keep
flows in hierarchical manner.

● Flow: It is created connecting different processors to transfer and modify data if
required from one data source or sources to another destination data sources.

● Processor: A processor is a java module responsible for either fetching data from
sourcing system or storing it in destination system. Other processors are also used
to add attributes or change content in flowfile.

● Flowfile: It is the basic usage of NiFi, which represents the single object of the
data picked from source system in NiFi. NiFi processor makes changes to flowfile 
while it moves from the source processor to the destination. Different events like
CREATE, CLONE, RECEIVE, etc. are performed on flowfile by different processors in
a flow.

● Event: Events represent the change in flowfile while traversing through a NiFi Flow.
These events are tracked in data provenance.

● Data provenance: It is a repository. It also has a UI, which enables users to check
the information about a flowfile and helps in troubleshooting if any issues that arise
during the processing of a flowfile.

# Apache NiFi Advantages

● Apache NiFi enables data fetching from remote machines by using SFTP and
guarantees data lineage.

● Apache NiFi supports clustering, so it can work on multiple nodes with same flow
processing different data, which increase the performance of data processing.

● It also provides security policies on user level, process group level and other
modules too.

● Its UI can also run on HTTPS, which makes the interaction of users with NiFi secure.

● NiFi supports around 188 processors and a user can also create custom plugins to
support a wide variety of data systems.

# Apache NiFi Disadvantages

● When node gets disconnected from NiFi cluster while a user is making any changes
in it, then the flow.xml becomes invalid. A node cannot connect back to the cluster
unless admin manually copies flow.xml from the connected node.

● Apache NiFi have state persistence issue in case of primary node switch, which
sometimes makes processors not able to fetch data from sourcing systems.

# Basic Concepts

Apache NiFi consist of a web server, flow controller and a processor, which runs on Java
Virtual Machine. It also has 3 repositories Flowfile Repository, Content Repository, and
Provenance Repository.

### Flowfile Repository
This repository stores the current state and attributes of every flowfile that goes through
the data flows of apache NiFi. The default location of this repository is in the root directory
of apache NiFi. The location of this repository can be changed by changing the property
named "nifi.flowfile.repository.directory".

### Content Repository
This repository contains all the content present in all the flowfiles of NiFi. Its default
directory is also in the root directory of NiFi and it can be changed using
"org.apache.nifi.controller.repository.FileSystemRepository" property. This directory uses
large space in disk so it is advisable to have enough space in the installation disk.

### Provenance Repository
The repository tracks and stores all the events of all the flowfiles that flow in NiFi. There
are two provenance repositories – volatile provenance repository (in this repository all
the provenance data get lost after restart) and persistent provenance repository. Its
default directory is also in the root directory of NiFi and it can be changed using
“org.apache.nifi.provenance.PersistentProvenanceRepository” and
“org.apache.nifi.provenance.VolatileProvenanceRepositor” property for the respective
repositories.

# Environment Setup

Step 1: Install the current version of Java in your computer. Please set the JAVA_HOME
in your machine

Step 2: Download Apache NiFi from https://nifi.apache.org/download.html

● For windows OS download ZIP file.

● For LINUX OS download TAR file.

● For docker images, go to the following link
https://hub.docker.com/r/apache/nifi/.

# Starting NiFi
Once NiFi has been downloaded and installed as described above, it can be started by using the mechanism appropriate for your operating system.

### For Windows Users
For Windows users, navigate to the folder where NiFi was installed. Within this folder is a subfolder named bin. Navigate to this subfolder and double-click the run-nifi.bat file.

This will launch NiFi and leave it running in the foreground. To shut down NiFi, select the window that was launched and hold the Ctrl key while pressing C.

### For Linux/macOS users
For Linux and macOS users, use a Terminal window to navigate to the directory where NiFi was installed. 

To run NiFi in the foreground, run 

          bin/nifi.sh run

This will leave the application running until the user presses Ctrl-C. At that time, it will initiate shutdown of the application.

To run NiFi in the background, instead run 

          bin/nifi.sh start. 

This will initiate the application to begin running. 

To check the status and see if NiFi is currently running, execute the command 

          bin/nifi.sh status
        
NiFi can be shutdown by executing the command               

          bin/nifi.sh stop.

Issuing bin/nifi.sh start executes the nifi.sh script that starts NiFi in the background and then exits. If you want nifi.sh to wait for NiFi to finish scheduling all components before exiting, use the --wait-for-init flag with an optional timeout specified in seconds: 

          bin/nifi.sh start --wait-for-init 120
          
If the timeout is not provided, the default timeout of 15 minutes will be used.

If NiFi was installed with Homebrew, run the commands nifi start or nifi stop from anywhere in your file system to start or stop NiFi.

### Installing as a Service
Currently, installing NiFi as a service is supported only for Linux and macOS users. To install the application as a service, navigate to the installation directory in a Terminal window and execute the command bin/nifi.sh install to install the service with the default name nifi. To specify a custom name for the service, execute the command with an optional second argument that is the name of the service. For example, to install NiFi as a service with the name dataflow, use the command bin/nifi.sh install dataflow.

Once installed, the service can be started and stopped using the appropriate commands, such as sudo service nifi start and sudo service nifi stop. Additionally, the running status can be checked via sudo service nifi status.

I Started NiFi. Now What?
The default installation generates a random username and password, writing the generated values to the application log. The application log is located in logs/nifi-app.log under the installation directory. The log file will contain lines with Generated Username [USERNAME] and Generated Password [PASSWORD] indicating the credentials needed for access. Search the application log for those lines and record the generated values in a secure location.

The following command can be used to change the username and password:

            $ ./bin/nifi.sh set-single-user-credentials <username> <password>

Now that NiFi has been started, we can bring up the User Interface (UI) in order to create and monitor our dataflow. To get started, open a web browser and navigate to https://localhost:8443/nifi. The port can be changed by editing the nifi.properties file in the NiFi conf directory, but the default port is 8443.

The web browser will display a warning message indicating a potential security risk due to the self-signed certificate NiFi generated during initialization. Accepting the potential security risk and continuing to load the interface is an option for development installations. The self-signed certificate will expire after 60 days. Production deployments should provision a certificate from a trusted authority and update the NiFi keystore and truststore configuration.

Accessing NiFi after accepting the self-signed certificate will display the login screen.

![image](https://user-images.githubusercontent.com/94011475/161213742-94e4e3f7-2833-4d7c-ac84-251604c3c23a.png)

Using the generated credentials, enter the generated username in the User field and the generated password in the Password field, then select LOG IN to access the system. This will bring up the User Interface, which at this point is a blank canvas for orchestrating a dataflow

# User Interface

Apache is a web-based platform that can be accessed by a user using web UI. The NiFi UI
is very interactive and provides a wide variety of information about NiFi. As shown in the
image below, a user can access information about the following attributes:

 Active Threads
 Total queued data
 Transmitting Remote Process Groups
 Not Transmitting Remote Process Groups
 Running Components
 Stopped Components
 Invalid Components
 Disabled Components
 Up to date Versioned Process Groups
 Locally modified Versioned Process Groups
 Stale Versioned Process Groups
 Locally modified and Stale Versioned Process Groups
 Sync failure Versioned Process Groups

# Components of Apache NiFi

### Processors

User can drag the process icon on the canvas and select the desired processor for the data flow in NiFi.

![image](https://user-images.githubusercontent.com/94011475/161202661-1764a32f-3c75-4c4c-8703-a5ced96e19a9.png)

![image](https://user-images.githubusercontent.com/94011475/161202551-3c8899d6-79d6-4fb8-a01e-b48984bc7cb1.png)

### Input port

Below icon is dragged to canvas to add the input port into any data flow. Input port is used to get data from the processor, which is not present in that process group.

![image](https://user-images.githubusercontent.com/94011475/161202680-d2c0404e-f9ec-420e-a5ca-b27749693420.png)

After dragging this icon, NiFi asks to enter the name of the Input port and then it is added to the NiFi canvas.

![image](https://user-images.githubusercontent.com/94011475/161202716-b7a52540-477f-4398-abc2-3afddb5910c6.png)

### Output port

The below icon is dragged to canvas to add the output port into any data flow.
The output port is used to transfer data to the processor, which is not present in that process group.

![image](https://user-images.githubusercontent.com/94011475/161202823-25901259-9a3c-4737-829d-9a3608f2721c.png)

After dragging this icon, NiFi asks to enter the name of the Output port and then it is added to the NiFi canvas.

![image](https://user-images.githubusercontent.com/94011475/161202844-b037b37e-e4e9-413a-bba0-61bf3f3ac2d4.png)

### Process Group

A user uses below icon to add process group in the NiFi canvas.

![image](https://user-images.githubusercontent.com/94011475/161202939-894c7a55-78b6-4f13-886c-07c1ffcaaa46.png)

After dragging this icon, NiFi asks to enter the name of the Process Group and then it is added to the NiFi canvas.

![image](https://user-images.githubusercontent.com/94011475/161202961-81586d43-25b3-493d-9781-37f9c40067a1.png)

### Remote Process Group

This is used to add Remote process group in NiFi canvas.

![image](https://user-images.githubusercontent.com/94011475/161202992-42a0b241-3b04-4a35-83c0-3cf6022690f3.png)

### Funnel

Funnel is used to transfer the output of a processor to multiple processors. User can use the below icon to add the funnel in a NiFi data flow.

![image](https://user-images.githubusercontent.com/94011475/161203022-dc35577b-a143-4136-89dc-50912efee974.png)

### Template

This icon is used to add a data flow template to NiFi canvas. This helps to reuse the data flow in the same or different NiFi instances.

![image](https://user-images.githubusercontent.com/94011475/161203052-53dc28c6-651a-489a-9b75-946c44f13eee.png)

After dragging, a user can select the templates already added in the NiFi.

### Label

These are used to add text on NiFi canvas about any component present in NiFi. It offers a range of colors used by a user to add aesthetic sense.

![image](https://user-images.githubusercontent.com/94011475/161203087-c46e02bf-dcc2-4596-88d9-8b88dc2d2d46.png)

# Processors

Apache NiFi processors are the basic blocks of creating a data flow. Every processor has different functionality, which contributes to the creation of output flowfile. Dataflow shown in the image below is fetching file from one directory using GetFile processor and storing it in another directory using PutFile processor.

![image](https://user-images.githubusercontent.com/94011475/161203546-4d0f20bb-6f66-4993-afa6-34c987baf399.png)

### GetFile
GetFile process is used to fetch files of a specific format from a specific directory. It also provides other options to user for more control on fetching. We will discuss it in properties section below.

![image](https://user-images.githubusercontent.com/94011475/161203633-136cda32-7868-4331-91cd-2ba518c33235.png)

GetFile Settings
Following are the different settings of GetFile processor −

Name
In the Name setting, a user can define any name for the processors either according to the project or by that, which makes the name more meaningful.

Enable
A user can enable or disable the processor using this setting.

Penalty Duration
This setting lets a user to add the penalty time duration, in the event of flowfile failure.

Yield Duration
This setting is used to specify the yield time for processor. In this duration, the process is not scheduled again.

Bulletin Level
This setting is used to specify the log level of that processor.

Automatically Terminate Relationships
This has a list of check of all the available relationship of that particular process. By checking the boxes, a user can program processor to terminate the flowfile on that event and do not send it further in the flow.

![image](https://user-images.githubusercontent.com/94011475/161203691-c9ccba5a-0b57-49a6-9e02-bf0e3e6e3c51.png)

GetFile Scheduling
These are the following scheduling options offered by the GetFile processor −

Schedule Strategy
You can either schedule the process on time basis by selecting time driven or a specified CRON string by selecting a CRON driver option.

Concurrent Tasks
This option is used to define the concurrent task schedule for this processor.

Execution
A user can define whether to run the processor in all nodes or only in Primary node by using this option.

Run Schedule
It is used to define the time for time driven strategy or CRON expression for CRON driven strategy.

![image](https://user-images.githubusercontent.com/94011475/161203800-3a6395b6-9f00-44f1-950c-c787b877a07e.png)

GetFile Properties
GetFile offers multiple properties as shown in the image below raging compulsory properties like Input directory and file filter to optional properties like Path Filter and Maximum file Size. A user can manage file fetching process using these properties.

![image](https://user-images.githubusercontent.com/94011475/161203867-a304c50f-b5f9-4337-b5d6-0a46c788e682.png)

GetFile Comments
This Section is used to specify any information about processor.

![image](https://user-images.githubusercontent.com/94011475/161203901-e68000cf-a338-473d-9fe3-3986ed8c6148.png)


### PutFile

The PutFile processor is used to store the file from the data flow to a specific location.

![image](https://user-images.githubusercontent.com/94011475/161204134-0da503ec-3bc7-4508-ba16-af833a7b33f9.png)

PutFile Settings
The PutFile processor has the following settings −

Name
In the Name setting, a user can define any name for the processors either according to the project or by that which makes the name more meaningful.

Enable
A user can enable or disable the processor using this setting.

Penalty Duration
This setting lets a user add the penalty time duration, in the event of flowfile failure.

Yield Duration
This setting is used to specify the yield time for processor. In this duration, the process does not get scheduled again.

Bulletin Level
This setting is used to specify the log level of that processor.

Automatically Terminate Relationships
This settings has a list of check of all the available relationship of that particular process. By checking the boxes, user can program processor to terminate the flowfile on that event and do not send it further in the flow.

![image](https://user-images.githubusercontent.com/94011475/161204181-47263046-abe2-4b54-8923-157fcd7040b7.png)

PutFile Scheduling
These are the following scheduling options offered by the PutFile processor −

Schedule Strategy
You can schedule the process on time basis either by selecting timer driven or a specified CRON string by selecting CRON driver option. There is also an Experimental strategy Event Driven, which will trigger the processor on a specific event.

Concurrent Tasks
This option is used to define the concurrent task schedule for this processor.

Execution
A user can define whether to run the processor in all nodes or only in primary node by using this option.

Run Schedule
It is used to define the time for timer driven strategy or CRON expression for CRON driven strategy.

![image](https://user-images.githubusercontent.com/94011475/161204230-86c2d74e-18ed-4910-9e9a-653309266e57.png)

PutFile Properties
The PutFile processor provides properties like Directory to specify the output directory for the purpose of file transfer and others to manage the transfer as shown in the image below.

![image](https://user-images.githubusercontent.com/94011475/161204276-07e0aa7f-8ae8-48a6-a91d-af1d6abf5526.png)

PutFile Comments
This Section is used to specify any information about processor.

![image](https://user-images.githubusercontent.com/94011475/161204327-83952654-9e0f-4690-b360-a3a7a93bac3f.png)
