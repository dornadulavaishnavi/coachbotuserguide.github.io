# Coachbot Swarm User Guide

Written and Maintained by Vaishnavi Dornadula (vaishnavidornadula2026@u.northwestern.edu)
Last Updated: February 19, 2024

We ask that you respect the system and help us keep it accessible to fellow academics by adhering to the guidelines explained in this guide. We reserve the right to refuse access to any individuals who are not courteous to the system or the Coachbot team.
If you have any questions, comments or concerns, please email us at coachbotswarmsystem@gmail.com and someone from our team will get back to you.

## Overview of System

### How Does the Swarm Function

#### Arena
![Arena and Play Area](https://github.com/dornadulavaishnavi/coachbotuserguide.github.io/assets/90789243/22bbe2c1-af4e-432a-ae49-c05bfe4c342a)

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

To use git through your preferred terminal, you must first download the appropriate packages. Follow this link to download Git for your OS: https://github.com/git-guides/install-git. Once you have downloaded git and checked for successful installation, you can close the repo. In the Github repo linked above, select the green “< > Code” dropdown button and copy either the https or ssh link. Which to choose is a matter of personal preference, but here is a reference to learn more about the differences: https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories.  In your terminal, navigate to where you want the local repo to be housed. Type *git clone* and paste the https or ssh link and hit enter. This will clone the repo to your local folder and you can now create your folder in the code queue. *git status* will tell you if there are any changes on your local system that have not been sent to the repo. Please remember to always *git pull* before you push and save a local copy of your code outside the repo. A quick guide to important and commonly used git commands can be found here: https://training.github.com/downloads/github-git-cheat-sheet/. The commands that will most commonly be used are *git pull, git status, git add, git commit,* and *git push*.

## Submitting your Code

Every submission to our system must be a folder with three files. The first is a .txt file called **email.txt** which simply contains the email address that should be contacted about e submitted code. The second file specifies the initial positions of the robots before the user code is run. Specifications of that file’s format and restrictions on robot positions are outlined in Section II.A.1. The third mandatory file is the code that will be uploaded to all active robots. This file, **usr_code.py**, must be written in python and formatted in the way outlined in Section II.A.2. The robots run python 2.7.16. There is a sample folder in the repo containing all three required files and a template for usr_code.py in the **Example_Folder**. Remember that your code should be placed in a folder in the **Code_Queue** folder to be run.

### Input Files

#### Example Submissions

Example Submission with these three mandatory files are located within the Example_Folder/Submission_Examples directory of the repository. These files will showcase various robot functionalities and are a good place to start familiarizing yourself with our platform and robot capabilities. To begin experimenting with the platform, we recommend taking a look at these files and editing them to create your first submission. Try changing the initial positions and number of robots in the **init_pose.csv** file or edit parameters to change behaviors such as how long the robots drive for or their LED color to understand how the API calls work. Be sure to change the email in the **email.txt** appropriately.

#### Initial Positions

The initial positions of each robot must be specified in a csv file named **init_pose.csv**. The values specified must follow the rules listed below.
- Each row should specify an ID number, x position, y position, and theta angle in radians. The ID number should be a whole number integer, while the x,y, and theta positions can be floats. 
- The play field is sized at -1.2m to 1.0m in the x and -1.4m to 2.35m in the y so the x and y positions must be within those dimensions. 
- There are currently 50 robots active in the Coachbot swarm so please limit your number of robots to 50.
- The ID number must be between 0 and 49.
- Each robot must start 25 cm away from each other.
- The x and y positions are in meters while the theta value is in radians (-2π, 2π) 

Example **init_pose.csv** file:

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

If your **init_pose.csv** file does not abide by the rules above, you will receive an email and can check the **input_pose_errors.csv** file for details on where it failed. 

#### User Code

The user code file must be named **usr_code.py** and be written in python. This same code will be uploaded to every robot that will run your code. Section III below explains the available robot functions and various functionality such as sending messages and logging. Instead of a main function, the robot code will look for a function called *usr(robot)* so be sure to add that to your code as shown below. It is also good practice to add a small delay in the while loop (See Section III.A.8 for function specifics).

**usr_code.py** format:

*imports  
def usr(robot):  
&emsp; # write code here  
&emsp; &emsp; while condition:  
&emsp; &emsp; &emsp; robot.delay() # defaults to 20 ms which is sufficient  
&emsp; &emsp; &emsp; # more code here  
return condition*  

The current time limit for code runtime is 10 minutes so if your code hits this limit, it will pause the code and return all the information it received until that point.

#### Email

The **email.txt** file should simply contain the email address all alerts should be sent to. Users will receive an email notification when their code begins to run and one when it has completed. The User may also instead receive an email letting them know that their initial positions were invalid or their code hit the time limit.

### GitHub Interface to the Coachbot System

The github repo to submit your code is located at https://github.com/dornadulavaishnavi/CoachbotSwarm/tree/main. Your code should be uploaded to the Code_Queue folder in the main branch of the repo. To gain access to push code to this repo, please send us an email to be added as a collaborator. Once you have access, clone the repo to your local computer using https or ssh. To avoid merge conflicts, please remember to *git pull* before you try to upload your code. Copy your required files into a uniquely named folder and be sure to note this name, as this will be the name of the folder containing the output of your run.

## Writing Code for the Coachbots

Check out our API Overview tutorial here for a quick introduction:

[![](https://markdown-videos-api.jorgenkh.no/youtube/Z8qkd0gtyGM)](https://youtu.be/Z8qkd0gtyGM)

### Available Robot Functions

#### robot.set_vel(left,right)

Parameters: left and right should be whole numbers between -50 and 50 that indicate wheel speeds corresponding to the respective wheel. 0 being no movement and 50 being the fastest possible speed. The negative values indicate that the wheel would spin backwards at that speed. These values have no unit.  
Output: none  
Example: *robot.set_vel(30,-40)*

#### robot.set_led(r,g,b)

Parameters: r,g,b should be integers between and 0 and 100 to set the color and brightness of the onboard LED  
Output: none  
Example: *robot.set_led(30,100,0)*

#### robot.virtual_id()

Parameters: none  
Output: An integer that is the virtual ID of the robot.   
Example: *virt_id = robot.virtual_id()*

#### robot.get_clock()

Parameters: none  
Output: a float of the number of seconds elapsed since the program started  
Example: *curr_time = robot.get_clock()*

#### robot.send_msg(msg)

Parameters: msg should be a string that is less than 64 bytes or it will be truncated. This msg can be the output of the struct.pack() function explained in the section below.  
Output: True is successful, False if not  
Example: *robot.send_msg(struct.pack(‘fffii’, float_0, float_1, float_2, int_0, int_1))*

#### robot.recv_msg()

Parameters: none  
Output: Returns the messages in the buffer since the last call of this function.   
Example: *msgs = robot.recv_msg()*

#### robot.get_pose()

Parameters: none  
Output: a list with the [x,y,theta], check to see that this output is valid before using it  
Example: *pose = robot.get_pose()*

#### robot.delay()

Parameters: default is 20ms but a different integer parameter can be specified  
Output: none  
Example: *robot.delay(500)*

### Sending and Receiving Messages

Sending and receiving messages is done through the *robot.send_msg()* and *robot.recv_msg()* functions explained above. The messages that these functions handle are created and read using *struct.pack()* and *struct.unpack()* so be sure to import struct at the top of your file if you plan to use messaging. For best results, add in a delay between any send and receive function calls. Example usage of these functions are shown below.

*Struct.pack()* example:  
*struct.pack(‘fffii’, float_0, float_1, float_2, int_0, int_1)*

The first argument, ‘fffii’, specifies the type of variables being sent in what order and quantity. In this example, I am sending three floats and two integers. The remaining parameters are the corresponding variables I am sending in the message

*Struct.unpack()* example:  
*struct.unpack(‘fffii’, msg_received[0][:24])*

The first argument, ‘fffii’ specifies the expected message content types. The second parameter specifies the variable I am reading from. Whatever variable I save the output of the *robot.recv_msg()* in will contain the entire buffer of messages. In this example, I am reading in the first message in the buffer and the [:24] specifies the message length, which is four times the number variables being sent.

### Logging from the Robots

Logging is a very useful debugging tool, especially in a swarm, where many robots are running the same code. To log messages from each robot, we write to a file instead of using print statements. These individual log files will be available to you after your code is run as explained in Section IV. In the **usr_code.py** file, add the following line of code to open the log file to write, *log = open(“experiment_log”, “wb”)*. The variable name of *log* can be different but the file being opened must be called *experiment_log* and it must be opened in binary write mode as indicated by the *wb*. To write to this file, use the write function with a string as the parameter *(log.write(string))*. Be sure to include the new line character *(\n)* at the end of your string so that each of your statements are on a new line. After every write, call the flush function *(log.flush())*. Be sure to close the file before your script returns *(log.close())*. 

## Getting the Results

When your code has finished running, you will receive an email from the system letting you know so. When you pull the repo, the **Completed_Runs** folder will have your results in your folder with the files explained below.

### Result Format

Within this folder, you should see the following directory tree (new files and directories are underlined).

&emsp; FolderName  
&emsp; &emsp; usr_code.py  
&emsp; &emsp; init_pose.csv  
&emsp; &emsp; email.txt  
&emsp; &emsp; <ins> init_pose_errors.csv </ins>  
&emsp; &emsp; <ins> output_logs </ins>  
&emsp; &emsp; &emsp; <ins> ID_mapping.csv </ins>  
&emsp; &emsp; &emsp; <ins> camera_video.mp4 </ins>  
&emsp; &emsp; <ins> #_logging.csv </ins>  
&emsp; &emsp; <ins> # </ins>  
&emsp; &emsp; <ins> automation_errors </ins>  

The **init_pose_errors.csv** will contain the contents of **init_pose.csv** or list any issues with the initial poses specified. The output_logs folder will hold all the outputs from the algorithm run. Since the ID you specify in the **init_pose.csv** file might not match the physical robot ID, the **ID_mapping.csv** file specifies which robot corresponds to which virtual ID. The .mp4 file is the recording of the run from our overhead raspberry pi camera. The logging files (**#_logging**) will be named with the virtual ID of the robot it pertains to and contain the position of the corresponding robot at every timestep of the run. This csv file is formatted in a timestep, x position, y position, theta angle in radians for each line. The # file is the virtual ID of the pertaining robot and will have any information you choose to write to the **experiment_log** file in your code. The **automation_errors** file will list any high level errors such as runtime limits or robots trying to exit the play field.

### Accessing the Output
Once you get an email that your code has finished running, you will be able to access your code’s output files in the **Completed_Runs** folder of the repo. Use the git pull command to load the folders onto your local machine and navigate to the folder with the unique name you had uploaded to the **Code_Queue** folder. Once you copy the contents of your folder to somewhere outside your repo, please delete your folder from the **Completed_Runs** and push your code. (Remember to always pull before pushing to avoid merge conflicts).

### Automation Error Messages:

The **automation_errors** file will contain information of high level errors such as hitting the runtime limit or robots leaving the playfield. This will not have any errors your user code may hit so please be sure to use the logging features to assist with debugging. 

<ins> Runtime limit </ins>: If you receive an email saying that your code hit the time limit, please make sure your code hits its return conditions properly or reduce the runtime of your code. You will still receive all the information above for the length of time your algorithm ran and access it in the same way.

<ins> Robot out of Bounds </ins>: If you receive an email or see in your **automation_errors** file that some robots went out of bounds, please make sure that your code keeps the robots within the playfield. The message in the file should specify the offending robot and the position it left the field to help with debugging. You will still receive all the information above for the length of time your algorithm ran and access it in the same way.

### Other Troubleshooting

<ins> Git Merge Conflict </ins> : If you see this error on your local computer when you attempt to push your code folder, first make sure you have a copy of this folder and its contents somewhere on your local computer outside of the repo. If you encounter a git merge error, please do not override anything at the Head. This simply means that your local repo is not up to date with the remote repo and what you are trying to push directly affects these differences. The easiest way is to keep the changes at the Head and check that what you’re uploading has a different name than any of the newly pulled folders. (Ex. if someone uploaded a folder named swarm_test which happens to be the folder name you were using, change your folder name and that should resolve the conflict)

<ins> No Push Access </ins>
: Make sure you go through the steps listed in Section I.C.1 and have received access to the system

If you run into any other issue or have any questions, please don’t hesitate to email us at coachbotswarmsystem@gmail.com.

## Simulation

Check out our Coachbot simulation here: https://github.com/michelleezhang/swarm-simulator. The README of this repo contains detailed instructions on how to download and use this tool.

## Coachbot FAQ

**Q**: The CoachbotSwarm Github repository says I do not have push access, how do I fix that?  
**A**: If you are unable to push to the repository, please make sure you have been granted contributor access. Email coachbotswarmsystem@gmail.com with your name, university (if applicable), and github username/email address you will be notified 

**Q**: I submitted my experiment but I no longer see it on the repository queue and did not receive any emails regarding the status of my experiment. Is there something wrong with the submission?  
**A**: There could be a few reasons why there were no alerts about the experiment.  Double check your spam folder to ensure that any experiment alerts have not accidentally ended up there.
The first most common reason would be that the swarm is currently charging and not running any experiments. In this case, the experiment is still queued up locally even if it is no longer on the repository’s queue. 
The second reason could be that the system could not find an **email.txt** file to send notifications to. If  this is the case, it will still attempt to run the experiment and you can find your results in the **Completed_Runs** folder of the repository in a folder with the same name as your submission.

**Q**: If I don’t care how many robots are used in my experiment or where they start, do I still need to submit an initial positions file?  
**A**: Yes, you will still need to submit an **init_pose.csv** file in your experiment for it to be run. Feel free to use the files provided in the **Example Folder** and edit as needed.
