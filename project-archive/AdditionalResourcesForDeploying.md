// Created By: Ethan Webb //

STEPS FOR DEPLOYING - These are the steps I took rather than using visual studio to manually point the solution towards the docker repositories since it did not work for me (the ec2 daemon did not like the security perms on images)
--------------------
EC2/DOCKER CREATION
1. Create both an AWS and Docker account.

2. Create two repositories on docker named 'bucstop' and 'gamemicro'

3. Create an ubuntu Ec2 on AWS. Click 'allow HTTP traffic' and also create a .pem key (can be named anything)

4. Open your local directory wherever the .pem key is stored and run CMD.

5. Go back to the EC2 instance and click 'connect'.

6. This should provide you with a copy/paste text (ubuntu@ec2-192.192.192.192)

7. Paste this along with the 'ssh -i .\'pemkeyname'.pem and you should be good. (You may need to remove inherited permissions on pem key because Windows may flag it)

8. Once in create an account using 'su adduser' and also grant them sudo privileges.

9. Switch users to said account and create a folder called 'scripts' under 'home'.

10. CD into the scripts folder and add the script files from github.
	- You can either manually create the files and copy/paste the contents in
	- OR sftp from your local machine (a little bit more time consuming)

11. Grant ./firstDeploy.sh permissions to execute (sudo chmod +x)


DOCKER PORTION / RUNNING SCRIPT THROUGH INSTANCE
1. Rebuild both solutions (from the sprint 2 branch on github)

2. Build Both Images (before deleting old solutions, go to file explorer and copy link
			FURTHERMORE, dont forget the '.' at the end for root)
	- docker build -f BucStop/Dockerfile -t 'name''/bucstop .
	- docker build -f GameMicroServer/Dockerfile -t 'name'/gamemicro .

3. Push Both Images (VIA CMD)
	- docker push 'namee'/bucstop
	- docker push 'name'/gamemicro

4.  Go to the EC2 instance and run './firstDeploy.sh'

ADDITIONAL INFO
1. If you're attempting to repush your new images (with new changes) and receieve a message saying that each layer already exists try this.
	- Within your cmd and location being the repository try docker rmi --force 'image id'
		- This should delete each of your images respectively allowing you to repush your new images with said changes.
