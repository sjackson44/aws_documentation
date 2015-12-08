# AWS Playbook - FIRSTBORN


###EC2 Instance:
	* Click on launch instance.
	* Choose an Amazon Machine Image.
	* Choose an instance type.
	* Configure instance details.
	* Add Storage.
	* Tag the Instance (ie key: Project, value: project_name).
	* Configure Security Group (make a new one or select an existing one).
	* Upload a key pair, or make a new one.
	* Review and launch.


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
	* Go back to the list of users, and add passwords to the the users you have just created.
		- To do this click on the name of the user you want to add a password too.
		- Scroll down to the user's profile, and click on the 'Manage Passwords' button, which will be located towards the right of the browser
		- Click assign custom password. 
		- Use a website like passwordsgenerator.net, or a program like OnePass to generate a strong password, use only upper and lower case letters, and numbers, do not use symbols, or other ambiguous characters, AWS will not accept passwords that contain these kinds of symbols.
		



###ELB:




###CloudFront:




###ElastiCache:


