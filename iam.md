#IAM

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