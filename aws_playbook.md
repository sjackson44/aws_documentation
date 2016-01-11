# AWS Playbook - FIRSTBORN


###EC2 Instance:
	* Click on launch instance.
	* Choose an Amazon Machine Image (We normally use Amazon Linux AMI).
	* Choose an instance type.
	* Configure instance details.
	* Add Storage.
	* Tag the Instance (ie key: Project, value: project_name).
	* Configure Security Group (make a new one or select an existing one). For development we usually use, 'Firstborn-only' and 'Internal'.
	* Upload a key pair, or make a new one, there are 2 ways to make a new one.
		1. (Preferred) Go to the EC2 Dashboard click on 'Key Pairs'
			-- Click on the 'Import Key Pair' button and select a key pair name, generate an ssh pub key on your local machine, and then copy/paste that into the 'Public key contents' box in the bottom.
		2. To make a key pair click where it says 'Choose an existing key pair' and select 'Create a new key pair', type in a name and click 'Download Key Pair' which will download a .pem file with a ssh private key you can use to access your EC2 instance remotely.  
	* Review and launch.
	* After the instance 


###RDS Instance:
	* Click on 'Launch DB Instance'.
	* Select a DB engine.
	* Determine whether or not you want Multi-AZ Deployment and Provisoned IOPS Storage as defaults for your instance (for certain production purposes).
	* Specify DB Details (here you make the db user name, password, and db name itself)
	* Configure Advanced VPC group and security group settings.
	* Launch.



###S3 Bucket:
	* Click create bucket, select a region.
	* Add a bucket policy to restrict user-client access.
	* Add a CORS policy to allow cross origin resource sharing between the client application and the server.
		- Bucket policies can be added by clicking on the magnifying glass next to the bucket name, clicking on permissions, clicking on 'Add bucket policy' and in the bottom left hand corner clicking on the AWS Policy Generator.
		- CORS configs can be made by clicking on the magnifiying glass next to the bucket name, clicking on 'Add CORS Configuration' and selecting 'Sample CORS Configurations' from the bottom left hand corner. Copy one of the examples and modify from there.



###IAM User:
	* Click on 'Users' on the side panel.
	* Click on 'Create New Users'.
	* Type in the name of up to five users.
	* Click on the 'Show User Security Credentials' button.
	* Copy the 'Access Key ID' and the 'Secret Access Key'.
	* Go back to the list of users, and add passwords (if you are creating a site.* IAM for a project it usually will not need a password and you can skip creating one) to the the users you have just created.
		- To do this click on the name of the user you want to add a password too.
		- Scroll down to the user's profile, and click on the 'Manage Passwords' button, which will be located towards the right of the browser
		- Click assign custom password. 
		- Use a website like passwordsgenerator.net, or a program like OnePass to generate a strong password, use only upper and lower case letters, and numbers, do not use symbols, or other ambiguous characters, AWS will not accept passwords that contain these kinds of symbols.
	* Select an user from the users list, scroll down and click on the 'Permissions' tag. Click on 'Create User Policy' under Inline Policies and create a policy for that user. Inline policies are controlled by the user account, whereas the above Managed Policies are controlled and managed by AWS. 
		- The 'Create User Policy' page will have two options 'Policy Generator' and 'Custom Policy', If you click on policy generator and hit the Select button you will be allowed to generate your own policy.
		- Make sure Effect is on Allow, under Actions check "all actions". Change Amazon Resource Name is on '*', and click 'Add Statement'
		- Here you can edit and finalize your policy, for quick reference take a quick look at other examples of dev/staging/production policies from the permissions section of other users and choose the scheme most relevant to you.
		- When you are done, click validate to make sure the policy does not have syntactical errors.
		
		



###ELB:
	* After logging in under the compute section of the 'Compute' section of the main dashboard, click on EC2.
	* On the left side scroll down until you see 'Load Balancers', click on this to begin configuring a load balancer instance
	* Click 'Create Load Balancer'
		- Give the load balancer a name
		- Firstborn already has a default VPC so leave that setting alone.
		- Click 'Add' and click on 'HTTPS (Secure HTTP)'.
	* Assign the appropriate security groups to the load balancer (Since we usually track our ELBs using Pingdom, load balancers Pingdom1 and Pingdom2 should be assigned as well, PingdomA and PingdomB should NOT be assigned as they were specific to an HBO project)
	* Select an SSL certificate to assign to the load balancer you can either upload a new one or choose an existing one (our existing default SSL cert is firstborn.wildcard)
	* Configure Health Check to these settings (unless custom settings are needed)
		- Response Timeout: 5 seconds
		- Health Check Interval: 15 seconds?
		- Unhealthy Threshold: 1?
		- Healthy Threshold: 10?
	* Add EC2 Instances
	* Add Tags (ie format:  Key = Project, Value = *project_name )
	* Review and Launch ELB instance, click 'Create' when you are finished.



###CloudFront:




###ElastiCache:
	* In the main AWS dashboard scroll to the Database section and click on 'ElastiCache'
	* Click on 'Launch Cache Cluster'
	* Click on the picture of the Redis icon, and click 'Next'
	* Turn off 'Enable Replication'
	* Select a size in the 'Node Type' section (we usually use either the cache.t2.micro for development, staging and production may vary in size depending on project)
	* Setup advanced configuration settings, leave 'Availablity Zones(s)' as 'No Preference'
	* Select a VPC Security Group (Firstborn only is usually the default security group for development caching servers hosted in our AWS, many staging and production servers are hosted on the clients AWS account, and may require the selection of different security groups)
	* Select 'Enable Automatic Backups'
	* Set the 'Back Up Retention' period to 7 days
	* Set the back up window to  6am UTC time (which will be either 6 or 7 hours ahead of Eastern time depending on daylight savings time)
	* Click on 'Select Window' in the 'Maintenance Window' section
	* Set the 'Start Day' on Sunday 
	* Set the Start Time to 1 hour ahead of whatever you set the Backup Window time to (ie if the Backup window is at 6am UTC, then the Maintenance Window should be at 7am)
		- Backup and maintenance windows can not occur within less than 30mins of each other.

