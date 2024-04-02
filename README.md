# Coachbot Swarm User Guide

Written and Maintained by Vaishnavi Dornadula (vaishnavidornadula2026@u.northwestern.edu)
Last Updated: February 19, 2024

We ask that you respect the system and help us keep it accessible to fellow academics by adhering to the guidelines explained in this guide. We reserve the right to refuse access to any individuals who are not courteous to the system or the Coachbot team.
If you have any questions, comments or concerns, please email us at coachbotswarmsystem@gmail.com and someone from our team will get back to you.

## Overview of System

### How Does the Swarm Function

#### Arena

The arena is shown above with the axis labeled and the play field highlighted. The play field runs from -1.2 to 1.0 meters in the x and -1.4 to 2.35 meters in the y. The arena houses charging rails for the robots along two of its walls and the swarm will charge between submissions if more than half the swarm is approaching a low voltage. 

#### Coachbots

The coachbots communicate over a server with each other and can do all-to-all communication. If you wish to restrict the communication radius, you must manually do that in your algorithm. A common way to do this is to send location along with the message so each robot can calculate its distance to the robot sending the message and discard it if it is outside the communication radius. For more information on sending messages, please refer to Section III.B. These purple, cylindrical robots have unique IDs which will be mapped to the initial positions file you submit to the repository (Section II.A.1). 

### Getting Started with Git

The Github repository to submit your code and access its results is located at https://github.com/dornadulavaishnavi/CoachbotSwarm/tree/main

#### Requesting Access to the Repo

To gain access to push your code to the repo, email us at coachbotswarmsystem@gmail.com with your name, university, and github username and/or email address associated with the account. This email could be different from the one you provide in Section II.A.3 to receive notifications on. You can find your github username by clicking on your profile picture in the top right corner and going to “Your Profile”. Your username will be underneath your large profile picture icon on the left side. We will email you when you have contributor access and you should be able to view a notification confirming this by clicking the tray icon in the upper right, next to your profile icon. If you already have git installed on your machine, skip ahead to Section II. If not, continue below for steps on installing git.

#### Github Desktop

Github Desktop is a convenient interface to utilize git tools without needing to use the terminal. Download the tool from https://desktop.github.com/. Look for the “Current Repository” Menu on the top left below the banner. In that dropdown menu, click “add” and select “Clone repository…”.  In the Github repo linked above, select the green “< > Code” dropdown button and copy either the https or ssh link. Which to choose is a matter of personal preference, but here is a reference to learn more about the differences: https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories. Once you have either the https or ssh link copied, go to Github Desktop and paste this link in the “URL” section. Make sure your local path points to where you want the repo to be housed and click the blue “clone” button. Now you should be able to pull by clicking “Pull Origin” in the top banner, see your changes on the left bar, commit changes in the bottom left corner, and push code with the button in the top banner. The option to push will not appear if you have no changes. Please remember to always pull before you push and save a local copy of your code outside the repo.  

#### Terminal

To use git through your preferred terminal, you must first download the appropriate packages. Follow this link to download Git for your OS: https://github.com/git-guides/install-git. Once you have downloaded git and checked for successful installation, you can close the repo. In the Github repo linked above, select the green “< > Code” dropdown button and copy either the https or ssh link. Which to choose is a matter of personal preference, but here is a reference to learn more about the differences: https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories.  In your terminal, navigate to where you want the local repo to be housed. Type git clone and paste the https or ssh link and hit enter. This will clone the repo to your local folder and you can now create your folder in the code queue. git status will tell you if there are any changes on your local system that have not been sent to the repo. Please remember to always git pull before you push and save a local copy of your code outside the repo. A quick guide to important and commonly used git commands can be found here: https://training.github.com/downloads/github-git-cheat-sheet/. The commands that will most commonly be used are git pull, git status, git add, git commit, and git push.

## Submitting your Code

Every submission to our system must be a folder with three files. The first is a .txt file called email.txt which simply contains the email address that should be contacted about e submitted code. The second file specifies the initial positions of the robots before the user code is run. Specifications of that file’s format and restrictions on robot positions are outlined in Section II.A.1. The third mandatory file is the code that will be uploaded to all active robots. This file, usr_code.py, must be written in python and formatted in the way outlined in Section II.A.2. The robots run python 2.7.16. There is a sample folder in the repo containing all three required files and a template for usr_code.py in the Example_Folder. Remember that your code should be placed in a folder in the Code_Queue folder to be run.

### Input Files

#### Example Submissions

Example Submission with these three mandatory files are located within the Example_Folder/Submission_Examples directory of the repository. These files will showcase various robot functionalities and are a good place to start familiarizing yourself with our platform and robot capabilities. To begin experimenting with the platform, we recommend taking a look at these files and editing them to create your first submission. Try changing the initial positions and number of robots in the init_pose.csv file or edit parameters to change behaviors such as how long the robots drive for or their LED color to understand how the API calls work. Be sure to change the email in the email.txt appropriately.

#### Initial Positions

The initial positions of each robot must be specified in a csv file named init_pose.csv. The values specified must follow the rules listed below.
- Each row should specify an ID number, x position, y position, and theta angle in radians. The ID number should be a whole number integer, while the x,y, and theta positions can be floats. 
- The play field is sized at -1.2m to 1.0m in the x and -1.4m to 2.35m in the y so the x and y positions must be within those dimensions. 
- There are currently 50 robots active in the Coachbot swarm so please limit your number of robots to 50.
- The ID number must be between 0 and 49.
- Each robot must start 25 cm away from each other.
- The x and y positions are in meters while the theta value is in radians (-2π, 2π) 
Example init_pose.csv file:
0,0.75,1.0,3.14
1,0.5,0.5,1
2,-0.5,-0.5,0
3,-0.1,-0.1,1
4,-1,-1,0
5,-0.5,0.5,1
6,0.5,-0.5,1
7,0.25,0.25,3.14
8,-0.25,0.8,2.5
9,0.75,-0.1,1.5

If your init_pose.csv file does not abide by the rules above, you will receive an email and can check the input_pose_errors.csv file for details on where it failed. 

#### User Code
The user code file must be named usr_code.py and be written in python. This same code will be uploaded to every robot that will run your code. Section III below explains the available robot functions and various functionality such as sending messages and logging. Instead of a main function, the robot code will look for a function called usr(robot) so be sure to add that to your code as shown below. It is also good practice to add a small delay in the while loop (See Section III.A.8 for function specifics).

usr_code.py format:
imports
def usr(robot):
	# write code here
	while condition:
		robot.delay() # defaults to 20 ms which is sufficient
		# more code here
return condition

The current time limit for code runtime is 10 minutes so if your code hits this limit, it will pause the code and return all the information it received until that point.
