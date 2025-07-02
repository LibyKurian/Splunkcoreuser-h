## Basic definition
Splunk as a software platform that you can use to search, analyze and visualize machine generated data.

So we have sources for data from these hosts:
- computers
- sensors
- virtual machines
- web servers
- network devices etc.

These hosts would typically generate data that falls into multiple categories (machine generated data):
- fault management
- configuration management
- accounting
- performance
- security
- system logs
- application logs
- metrics
- tickets

To get insights from these data, we put it into centralized management tool that is Splunk, And Splunk mainly has two categories of components:

- Processing components
	1. indexers.
	2. forwarders
	3. search heads.
- Management components (manage the processing components)
	1. deployment server
	2. indexer cluster manager
	3. search head cluster deployer
	4. license manager
	5. monitoring console.

After we can connect through one of the Splunk components that is referred to as a search head.

And then we can 
- search
- analyze
- visualize data,
or create things like 
- reports
- alerts
- dashboards
- knowledge

## Splunk components
### Forwarders
Generally installed on host machines to collect data and send it to Splunk. There are two types of Forwarders:
1. Universal Forwarders
	Heavily used in production environment
	Separate executable file for this  which has reduced functionality 
2. Heavy Forwarders
	It can parse data before sending
	It set up from Splunk Enterprise package file and configured as this not an separate executable file

### Indexers(Search peer)
Its a Splunk Enterprise instance and this component is which receives, processes, and writes it into disk.
Data from Hosts >> Indexer >> Disk
- Processing
	- Transform raw data into events
	- Assign Metadata - source, sourcetype, host
	- Timestamps
- Repositories are known as Indexes
- And these repo structured in sub categories:
	- Home Path
		- Hot Bucket (most Active)
		- Warm Bucket
	- Cold Path
		- Cold Bucket
	- Thawed Path
		- Frozen to Thawed bucket
- depending on time and size constraints that you set, these data get rolled over from top to bottom(Hot > Warm > Cold ...)
- For Data Availability we have data replication which is managed by Cluster Manager
### Search Heads
From all the indexers it contributed to search heads
This is where we write search queries (SPL)
Cluster Captain for coordinating job scheduling 
Cluster Deployer to distribute apps

### Deployement Server
Distributes content to Deployment clients
A facility of single server which can deploy apps to similar type of thousands of forwarders we have in a prod environment.
Like Windows forwarders or Linux Forwarders

### License Manager
Its a centralised manger which holds the limit of things we can do
like 500 gb of data in a day, or CPU usage limit etc

### Monitoring Console
Display topology of like hosts , dashboards , overall whats going on.

```
                                                ║    ⚡ PENDING NOTES LOADING ⚡  ║
                                                ║           ▓▓▓▓▓▓▓▓ 85%           ║
```
