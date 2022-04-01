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

The general features of Apache NiFi are as follows:

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

The key concepts of Apache NiFi are as follows:

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
