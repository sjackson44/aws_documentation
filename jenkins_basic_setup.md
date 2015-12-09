#Jenkins Playbook - FIRSTBORN

#Install Java and Git on your Jenkins Server

* Make sure you have Java7 or Java8(preferable) installed on your local machine.
	- To check and see if you have java type "java -version" in the terminal of your local machine
	- If you do not have Java installed install it on your machine. 
		- Red Hat Distros - "sudo yum install java"
		- Ubuntu (if yum is not installed) - "sudo apt-get install default-jdk"
* Make sure git installed on your Jenkins Server as well, if it is not already.

#Setup Basic Login Credentials

* Go to "Manage Jenkins" --> "Configure Global Security"
* Click "Enable security"
* Click "Jenkins' own user database", and check box "Allow Users to sign up"
* In the "Authorization" section make sure "Anyone can do anything" is clicked"
* Click "Save"

#Private SSH Key
* Use your clone ssh url from git repo.
* Add your Git repo's SSH Private key (~/.ssh/id_rsa not ~/.ssh/id_rsa.pub) to the Credentials (key can be found on the Git repo service you are using ie Github, BitBucket Server, etc)
	- Set the scope and user name.
	- In Credentials click 'Enter directly' and make sure SSH id_rsa private key is inserted and any passphrase that you have is also written in to the passphrase section.
	- Click "Save".

#Install Appropriate GIT plugins

* Go to "Manage Jenkins" --> "Manage Plugins" 
	- Inside manage plugins use the Filter bar to look for two plugins you need to install "GIT client plugin" and "GIT plugin"
	- Click the check box for both and then click the "Download now and install after restart" button

#Configure GIT plugins

* Go to "Configure System" by going from Home --> Manage Jenkins --> Configure System
	- Scroll down in Configure System until you see the Git section
	- Add the path where git is located on your Jenkins Server in the "Path to Git executable" section. (Usually "/usr/bin/git" but if unsure type 'which git' in your local machines terminal)
	- Additionally click on the "Install automatically" check box.
	- Click "Save" or "Apply" 

#Configure Project for Build Testing

* Click on the name of your project, found on your home screen, this will take you into your project folder.
* Click on the "Configure" button on the left.
	- Give the project a name if it does not have one and a description if you want.
	- Click on the 'Git' button (if this is not there you did not install the GIT Client plugin or you did and need to restart jenkins) Enter the "Repository URL" (We are using the ssh version of it which can be found when you click 'Clone' on the Git repo you want to build with i.e. ssh://git@git.firstborn.com:7999/~user.name/jenkins-test.git)
	- Click on the "Credentials" button and select your SSH key, if does not exist click the "Add" button next to the key and make one.
	- Click "Save"
	