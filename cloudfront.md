#Cloudfront

###Cloudfront:
	* In the main AWS dashboard scroll to the Database section and click on 'Cloudfront'
	* Click 'Create Distribution'
	* Under the 'Select a delivery method for your content' page there is a section called 'Web' click on the 'Get Started' section under that.
	* Under Origin Settings make sure you:
		- Find the s3 origin (or other relevant origin, if s3 you should have already set up an s3 bucket, go to s3.md and set one up if you have not already done so), place this in the 'Origin Domain Name' section.
		- Leave the origin path blank (defaults to root)
		- For 'Origin ID' put the first portion of the s3 tag in (ie if your s3 tag says example.s3-website-us-east-1.amazonaws.com, then the Origin ID is 'example')
		- Leave the 'Custom Headers'
	* Under 'Default Cache Behavior Settings' make sure you:
		- Check HTTP and HTTPS for 'Viewer Protocol Policy'
		- Check the 'GET,HEAD' button under 'Allowed HTTP Methods'
		- Leave 'Forward Headers', 'Object Caching', 'Forward Cookies', 'Forward Query Strings', 'Smooth Streaming', and 'Restrict User Access' at their defaults
		- Click 'yes' under 'Compress Objects Automatically'