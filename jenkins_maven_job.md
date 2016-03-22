#Jenkins Maven Job (For Java Development)

	* Go to the homepage click on 'New Item' in the left corner.
	* Enter a name in 'Item name' and click on 'Maven project', then click 'Okay'
	* Java is a compiled language and needs a compiler to run, it for the purposes of Jenkins this means installing a plugin that can handle a JDK (Java Developer Kit) that can compile .java files into .jar format.
		- Go to the homepage click on 'Manage Jenkins', then click 'Manage Plugins'
		- Click the 'Available' tab and then search under the term 'JDK', install the plugin 'JDK Parameter Plugin', install it and then restart jenkins
		- At the homepage again click on 'Manage Jenkins' and then 'Configure System'
		- Scroll down to JDK and click the button
			- Add a name to the parameter you want
			- Add a path to 'JAVA_HOME' where you JDK install is (your ec2 user script should have installed it in /usr/lib but if not you'll have to install it on the jenkins server manually, if you do not click 'Install Automatically' you will have to also change the name of the JAVA_HOME variable manually in the jenkins server as well)
			- Click 'Save'

##Configure Project for Build Testing
	* Click on the "Configure" button on the left.
		- Enter a name and select the 'Default JDK'
		- Give the project a name if it does not have one and a description if you want.
	* Fill out the 'Maven Project Name' and make sure to click 'Discard Old Builds' and discard 3
	* Click on the name of your project, found on your home screen, this will take you into your project folder.
	* Click 'This build is parameterized' and select 'JDK Parameter'
	* Click on the 'Git' button (if this is not there you did not install the GIT Client plugin or you did and need to restart jenkins) Enter the "Repository URL" (We are using the ssh version of it which can be found when you click 'Clone' on the Git repo you want to build with i.e. ssh://git@git.firstborn.com:7999/~user.name/jenkins-test.git)
		- Click on the "Credentials" button and select your SSH key, if does not exist click the "Add" button next to the key and make one.
		- In 'Branches to build' select the branch you want to pull from
	* Under the 'Build' section make sure to point towards the pom.xml from the root of the git repo you have pulled in. / is implied so you do not need to write it in (ie dev/example-to-pom/pom.xml)
	* Click "Save"

	