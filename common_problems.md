#Common Problems And Troubleshooting

###ELB
	* 5xx Level Healthcheck Errors
		- These errors are ELBs generic way of saying a server is down, they provide no explaination as to what actually happened. If you curl the path it will just say 5xx.
		- To get around this curl the actual ec2 instance(s) attached to the ELB, this will give you the actual status error that is breaking the app.
	* 302 Infinite Loop Error
		-  Infinite loops can occur between a server and the ELB instance in numerous ways one of the more common is when both the ELB and backend app have been set up to look for SSL. 
			- Ex. Your ELB terminates SSL for the user when the user enters the right DNS, the ELB passes the user to the backend where the app, looking for https protocols and not seeing them, does not trust the request, attaches https and sends it back to the ELB, which in turn terminates SSL again and sends it to the app, this loop continues until the backend timesout or the ELB instance fails it's healthcheck (a ping test that looks for a 200 status return)
		- To solve for this without removing the ELB and having to run SSL directly through the ec2 instance(s) (impossible if you have multiple instances hosting the same site backend) make sure the app can trust the proxy headers that are coming from the load balancer, this can be done in a variety of ways depending on the backend. That way the ELB is the only one handling SSL.

###Jenkins - Git 
	* Fatal: The Remote End Hung Up Unexpectedly, early EOF, index-pack failed
		- Can be caused by a number of things but is usually related to a failure of git to 


###S3
	* HTTPS failure
		- S3 by itself can not handle https calls, this is usually done by a load balancer or cloud front. Make sure s3 takes HTTP only.
	* No PHP in Document Root
		- Browsers can not process PHP do not put it in the document root, if the s3 bucket servers and index.php file to the browser
