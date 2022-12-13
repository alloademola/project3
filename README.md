# project3-MERN
Backend Configuration Settings
Update ubuntu on your EC2
sudo apt update
<img width="1440" alt="Screenshot 2022-12-13 at 12 31 47" src="https://user-images.githubusercontent.com/118350020/207307173-018eed57-6951-4ec7-8746-e87e398761fd.png">
how it looks like after updating 
<img width="1440" alt="Screenshot 2022-12-13 at 12 34 04" src="https://user-images.githubusercontent.com/118350020/207307547-bd07cc13-004a-45e4-8ae7-b0700745684d.png">

Upgrade ubuntu

sudo apt upgrade
<img width="1440" alt="Screenshot 2022-12-13 at 12 45 18" src="https://user-images.githubusercontent.com/118350020/207309522-0255a2b2-9270-4c02-bda0-47684c75332f.png">

getting the location of Node.js software from Ubuntu repositories.
using.   curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
<img width="1440" alt="Screenshot 2022-12-13 at 12 47 56" src="https://user-images.githubusercontent.com/118350020/207310154-483f7800-0d34-4022-a257-08fc90dab638.png">
To Install Node.js on the server
We are going to use this command below

sudo apt-get install -y nodejs
<img width="1440" alt="Screenshot 2022-12-13 at 12 53 32" src="https://user-images.githubusercontent.com/118350020/207311569-35500af3-aad5-474f-ba87-99b872e6d14c.png">

Note: The command above installs both nodejs and npm. NPM is a package manager for Node like apt for Ubuntu, it is used to install Node modules & packages and to manage dependency conflicts.

So to Verify the node installation we are going to use this command below
node -v 
npm -v 

Application Code Setup
So now , we are going to Create a new directory for our To-Do project: using this command below
mkdir Todo

Run the command below to verify that the Todo directory is created with ls command

Note:  In order to see some more useful information about files and directories, you can use the following combination of keys, ls -lih – 
it will show you different properties and size in human readable format. 
You can learn more about different useful keys for ls command with ls --help.

Now change your current directory to the newly created one:using 
cd Todo

Next, we are going to use the command npm init to initialise our project, so that a new file named package.json will be created.
This file will normally contain information about your application and the dependencies that it needs to run. 
Follow the prompts after running the command. 
You can press Enter several times to accept default values, then accept to write out the package.json file by typing yes.

using this command below
npm init

<img width="1440" alt="Screenshot 2022-12-13 at 13 40 55" src="https://user-images.githubusercontent.com/118350020/207320835-231fc9ef-2627-4148-9fae-158e8d3694ed.png">

so we need to run command ls to confirm that we have package.json file created.


