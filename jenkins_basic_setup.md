#Jenkins Playbook - FIRSTBORN

(If you have an user data script)
#


(If you have to install it on the server manually) 
#Install Java and Git on your Jenkins Server

* Make sure you have Java7 or Java8(preferable) installed on your local machine.
	- To check and see if you have java type "java -version" in the terminal of your local machine
	- If you do not have Java installed install it on your machine. 
		- Red Hat Distros - "sudo yum install java"
		- Ubuntu (if yum is not installed) - "sudo apt-get install default-jdk"
* Make sure git installed on your Jenkins Server as well, if it is not already.
------------------------------


#Setup Basic Login Credentials

* Go to "Manage Jenkins" --> "Configure Global Security"
* Click "Enable security"
* Click "Jenkins' own user database", and check box "Allow Users to sign up"
* In the "Authorization" section make sure "Anyone can do anything" is clicked"
* Click "Save"

#Private SSH Key
<<<<<<< HEAD
* Add your Jenkins pub key to your git repo (~/.ssh/id_rsa.pub not ~/.ssh/id_rsa) (go to your git repo through the client, on Stash once you get to the repo, click on settings on the left and then click on 'add access key' copy the jenkins server pub key here)
* Create a credential in credentials to allow Jenkins to pass it's private key (~/.ssh/id_rsa)
	- Go to the homepage click on 'Credentials' click on 'Global credentials', and on the left click 'Add Credentials'.
	- Set the scope and user name.
	- In Credentials click 'Enter directly' and make sure SSH id_rsa private key is inserted and any passphrase that you have is also written in to the passphrase section.
	- Click "Save".
* If you have ec2 instances you will also have to follow the same process to allow your jenkins server access to your ec2 instances. You can even use the jenkins public/private keys to do this if you want. If you want unique keys you can generate a public and private key pair on any machine you want, learn more here [How to generate SSH Keys][1]. Make sure to make a credential with the private key (like you did with the jenkins key) and put the public key in the ec2 server(s)
	- ssh into the ec2 instance and open ~/.ssh/authorized_keys with nano (will probably need to use sudo mode ie sudo nano ~/.ssh/authorized_keys) enter the public key that matches the private key of the credential. (This is the manual way to do it, if you have and ran a provision-ssh-keys.sh script this will have already been done for you)


[1]: https://help.github.com/articles/generating-an-ssh-key/ "How to generate SSH Keys"
=======
* Use your clone ssh url from git repo.
* Add your Git repo's SSH Private key (~/.ssh/id_rsa not ~/.ssh/id_rsa.pub) to the Credentials (key can be found on the Git repo service you are using ie Github, BitBucket Server, etc)
	- Set the scope and user name.
	- In Credentials click 'Enter directly' and make sure SSH id_rsa private key is inserted and any passphrase that you have is also written in to the passphrase section.
	- Click "Save".
	