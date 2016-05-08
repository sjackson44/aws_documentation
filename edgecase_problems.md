##Edge Case Scenarios

###Jenkins Servers

	###Problem

	- Normally when Pingdom pings a site protected by a login screen it can easily hit the site and receive a 200 status.
	- However for password protected Jenkins servers hitting the URL directly at root results in failure as Jenkins will demand authentication and prevent a 200 status unless it receives it.


	###Solution

	-There are two solutions
		1. Click on the name of the server you want to edit, click on the optional tag, and add the username and password directly to the check parameters. Click 'Modify Check' when you are finished.
		2. Add "/login?from=%2F" after the root URL of the DNS name. ie "example-jenkins.fborn.com/login?from=%2F". This will also prevent you from having to type the username and password credentials directly into the websites Pingdom editing board.

