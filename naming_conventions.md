#Naming Conventions


##AWS
```
	* All EBS (EC2, ELB(Load Balancers), RDS, Elasticache) instances should two different key-value pairs, Name and Project.
		Key           Value
		Name          Project Name (capitalized first letters and spaces)
		Project		  project (lowercased one word name of client company)
```

##Stash (Bit Bucket Server)
```
	*Project bucket names should be the name of the client (company) with the first letter of each major word capitalized, and appropriate spaces used (ie. Cycle for Survival, ie. Dentsu)
	*Repo level names should follow similar protocol to project bucket names, with two additions.
		- The anme of the project bucket should be added to the beginning of the repo name.
		- The year should be added at the end of the repo name
		- (ie. Dew All Star Game 2016)
```