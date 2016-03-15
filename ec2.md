#EC2

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
