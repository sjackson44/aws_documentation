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

###Common Cases
	* 5xx Level Healthcheck Errors
		- These errors are ELBs generic way of saying a server is down, they provide no explaination as to what actually happened. If you curl the path it will just say 5xx.
		- To get around this curl the actual ec2 instance(s) attached to the ELB, this will give you the actual status error that is breaking the app.
	* 302 Infinite Loop Error
		-  Infinite loops can occur between a server and the ELB instance in numerous ways one of the more common is when both the ELB and backend app have been set up to look for SSL. 
			- Ex. Your ELB terminates SSL for the user when the user enters the right DNS, the ELB passes the user to the backend where the app, looking for https protocols and not seeing them, does not trust the request, attaches https and sends it back to the ELB, which in turn terminates SSL again and sends it to the app, this loop continues until the backend timesout or the ELB instance fails it's healthcheck (a ping test that looks for a 200 status return)
		- To solve for this without removing the ELB and having to run SSL directly through the ec2 instance(s) (impossible if you have multiple instances hosting the same site backend) make sure the app can trust the proxy headers that are coming from the load balancer, this can be done in a variety of ways depending on the backend. That way the ELB is the only one handling SSL.
