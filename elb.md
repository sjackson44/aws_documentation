#Elastic Load Balancer (ELB)

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

