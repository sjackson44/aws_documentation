#Elasticache

###ElastiCache:
	* In the main AWS dashboard scroll to the Database section and click on 'ElastiCache'
	* Click on 'Launch Cache Cluster'
	* Click on the picture of the Redis icon, and click 'Next'
	* Turn off 'Enable Replication'
	* Select a size in the 'Node Type' section (we usually use either the cache.t2.micro for development, staging and production may vary in size depending on project)
	* Setup advanced configuration settings, leave 'Availablity Zones(s)' as 'No Preference'
	* Select a VPC Security Group (Firstborn only is usually the default security group for development caching servers hosted in our AWS, many staging and production servers are hosted on the clients AWS account, and may require the selection of different security groups)
	* (Only do this if the redis db is larger than a small) Select 'Enable Automatic Backups'
	* Set the 'Back Up Retention' period to 7 days
	* Set the back up window to  6am UTC time (which will be either 6 or 7 hours ahead of Eastern time depending on daylight savings time)
	* Click on 'Select Window' in the 'Maintenance Window' section
	* Set the 'Start Day' on Sunday 
	* Set the Start Time to 1 hour ahead of whatever you set the Backup Window time to (ie if the Backup window is at 6am UTC, then the Maintenance Window should be at 7am)
		- Backup and maintenance windows can not occur within less than 30mins of each other.