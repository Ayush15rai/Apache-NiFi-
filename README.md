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
● For UNIX OS download TAR file.
● For docker images, go to the following link
https://hub.docker.com/r/apache/nifi/.

Step 3: The installation process for Apache NiFi is very easy. The process differs with the OS:

● Windows OS: Unzip the zip package and the Apache NiFi is installed.
● UNIX OS: Extract tar file in any location and the Logstash is installed.

                     $tar –xvf nifi-1.6.0-bin.tar.gz
                     
Step 4: Open command prompt, go to the bin directory of NiFi. For example, C:\nifi1.7.1\bin, and execute run-nifi.bat file.

                      C:\nifi-1.7.1\bin>run-nifi.bat

Step 5: It will take a few minutes to get the NiFi UI up. A user can check nifi-app.log,
once NiFi UI is up then, a user can enter http://localhost:8080/nifi/ to access UI.

# Apache NiFi — User Interface

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



