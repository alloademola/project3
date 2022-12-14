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
<img width="1440" alt="Screenshot 2022-12-13 at 13 56 38" src="https://user-images.githubusercontent.com/118350020/207324365-1fef99b9-c424-4cde-bf72-b6d8c661e948.png">
done.

Next step is to Install ExpressJs and create the Routes directory.

To Install ExpressJS
We need to Remember that, Express is a framework for Node.js, therefore a lot of things developers would have programmed is already taken care of out of the box. 
In that case, it simplifies development, and abstracts a lot of low level details. 
For example, Express helps us, to define routes of your application based on HTTP methods and URLs.

To use express, we need to install it, using npm
npm install express
<img width="1440" alt="Screenshot 2022-12-13 at 14 12 28" src="https://user-images.githubusercontent.com/118350020/207327447-921cf945-6bfe-4820-8ca3-d93c5ee741de.png">

Now we are going to Now create a file called  index.js with the command below

touch index.js
and after that, we need 
Run ls to confirm that our index.js file is successfully created

<img width="1440" alt="Screenshot 2022-12-13 at 14 17 46" src="https://user-images.githubusercontent.com/118350020/207328342-c6cb47dd-0bac-40fa-ab4d-fdc9622431a1.png">
Now we are going to, Install the dotenv module using the command below.
npm install dotenv

<img width="1440" alt="Screenshot 2022-12-13 at 14 19 57" src="https://user-images.githubusercontent.com/118350020/207328885-06903c14-6ad7-4036-968b-6a598371e606.png">

now we are going to 
Open the index.js file with the command below
vim index.js

<img width="1440" alt="Screenshot 2022-12-13 at 14 31 44" src="https://user-images.githubusercontent.com/118350020/207335834-127aca3c-5ca1-4797-bed8-ed543a6d604e.png">
Type the code below into it and save.

const express = require('express');
require('dotenv').config();

const app = express();

const port = process.env.PORT || 5000;

app.use((req, res, next) => {
res.header("Access-Control-Allow-Origin", "\*");
res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
next();
});

app.use((req, res, next) => {
res.send('Welcome to Express');
});

app.listen(port, () => {
console.log(`Server running on port ${port}`)
});

<img width="1440" alt="Screenshot 2022-12-13 at 14 36 49" src="https://user-images.githubusercontent.com/118350020/207337929-b14a1462-1126-487f-bd05-48055e0d471c.png">

Notice that we have specified to use port 5000 in the code. This will be required later when we go on the browser.

Use :w to save in vim and use :qa to exit vim

Now it is time to start our server to see if it works. Open your terminal in the same directory as your index.js file and type:
so we are using the command below
node index.js

<img width="1440" alt="Screenshot 2022-12-13 at 14 40 56" src="https://user-images.githubusercontent.com/118350020/207340935-393afb98-e62b-4fe3-bbf7-f18ee186d76d.png">

Now we need to open this port in EC2 Security Groups. Refer to Project 1 Step 1 – Installing the Nginx Web Server. There we created an inbound rule to open TCP port 80, you need to do the same for port 5000, like this:

<img width="1440" alt="Screenshot 2022-12-14 at 11 59 25" src="https://user-images.githubusercontent.com/118350020/207577721-084d6608-ac31-4f6a-9583-ea089ae0007e.png">

Now Open up your browser and try to access your server’s Public IP or Public DNS name followed by port 5000:
so youu will get this outcome below

<img width="1440" alt="Screenshot 2022-12-14 at 12 00 52" src="https://user-images.githubusercontent.com/118350020/207578105-08d7eaed-2534-4cce-8477-2a222f9d77e0.png">

next step is 
Routes
There are three actions that our To-Do application needs to be able to do:

Create a new task
Display list of all tasks
Delete a completed task
Each task will be associated with some particular endpoint and will use different standard HTTP request methods: POST, GET, DELETE.

For each task, we need to create routes that will define various endpoints that the To-do app will depend on. So let us create a folder routes
Now run this command below

mkdir routes

<img width="1440" alt="Screenshot 2022-12-14 at 12 16 26" src="https://user-images.githubusercontent.com/118350020/207581397-c29049f7-2f92-4135-9a62-0ebbb0777e12.png">

You can as well, open multiple shells in Putty or Linux/Mac to connect to the same EC2

Change directory to routes folder.
so use these command below

cd routes

so after that, you can now, create a file api.js with the command below

touch api.js

so thereafter, you can now open the file below

vim api.js

<img width="1440" alt="Screenshot 2022-12-14 at 12 21 46" src="https://user-images.githubusercontent.com/118350020/207582482-af975a80-0733-48fc-8e64-f79de3dd33e3.png">

Copy below code in the file.

const express = require ('express');
const router = express.Router();

router.get('/todos', (req, res, next) => {

});

router.post('/todos', (req, res, next) => {

});

router.delete('/todos/:id', (req, res, next) => {

})

module.exports = router;

So moving forward ,let create Models directory.

MODELS
Now comes the interesting part, since the app is going to make use of Mongodb which is a NoSQL database, we need to create a model.

A model is at the heart of JavaScript based applications, and it is what makes it interactive.

We will also use models to define the database schema . This is important so that we will be able to define the fields stored in each Mongodb document. (Seems like a lot of information, but not to worry, everything will become clear to you over time. I promise!!!)

In essence, the Schema is a blueprint of how the database will be constructed, including other data fields that may not be required to be stored in the database. These are known as virtual properties

To create a Schema and a model, install mongoose which is a Node.js package that makes working with mongodb easier.

Change directory back Todo folder with cd .. and install Mongoose

So after changing your Folder back to Todo, now run this command below to install Mongoose

npm install mongoose

<img width="1440" alt="Screenshot 2022-12-14 at 12 40 17" src="https://user-images.githubusercontent.com/118350020/207585866-970775af-06d0-46cd-94cb-0ba7c88f231f.png">

Now Create a new folder models :
Using this command below

mkdir models
<img width="1440" alt="Screenshot 2022-12-14 at 12 44 45" src="https://user-images.githubusercontent.com/118350020/207586940-ad683e68-4510-4249-82f0-711361a59252.png">

MODELS
 next step is Change the directory into the newly created ‘models’ folder with
 cd models
 
 <img width="1440" alt="Screenshot 2022-12-14 at 12 49 12" src="https://user-images.githubusercontent.com/118350020/207587945-13e35c1f-2b61-4c70-abc4-023de8b19ff1.png">

So Inside the models folder, we are going to create a file and name it todo.js with the command below

touch todo.js
<img width="1440" alt="Screenshot 2022-12-14 at 12 51 27" src="https://user-images.githubusercontent.com/118350020/207588296-c8c47128-d6dd-43ef-af48-54fdc185e8e5.png">

Note: All the three commands above, can be defined in one line, to be executed consequently with help of && operator, like this:
mkdir models && cd models && touch todo.js

Open the file created with vim todo.js then paste the code below in the file:

const mongoose = require('mongoose');
const Schema = mongoose.Schema;

//create schema for todo
const TodoSchema = new Schema({
action: {
type: String,
required: [true, 'The todo text field is required']
}
})

//create model for todo
const Todo = mongoose.model('todo', TodoSchema);

module.exports = Todo;

<img width="1440" alt="Screenshot 2022-12-14 at 13 00 12" src="https://user-images.githubusercontent.com/118350020/207590188-6dcbf7c7-39fe-45af-ae58-ba9bf33643a6.png">

Now we are going to update our routes from the file api.js in ‘routes’ directory to make use of the new model.

In Routes directory, open api.js with vim api.js, delete the code inside with :%d command and paste there code below into it then save and exit

we are using this command below

vim api.js

<img width="1440" alt="Screenshot 2022-12-14 at 13 12 28" src="https://user-images.githubusercontent.com/118350020/207592358-d390e7e1-8da5-4056-9834-bef17148deca.png">

so now, we are going to paste the code below into it then save and exit

const express = require ('express');
const router = express.Router();
const Todo = require('../models/todo');

router.get('/todos', (req, res, next) => {

//this will return all the data, exposing only the id and action field to the client
Todo.find({}, 'action')
.then(data => res.json(data))
.catch(next)
});

router.post('/todos', (req, res, next) => {
if(req.body.action){
Todo.create(req.body)
.then(data => res.json(data))
.catch(next)
}else {
res.json({
error: "The input field is empty"
})
}
});

router.delete('/todos/:id', (req, res, next) => {
Todo.findOneAndDelete({"_id": req.params.id})
.then(data => res.json(data))
.catch(next)
})

module.exports = router;

<img width="1440" alt="Screenshot 2022-12-14 at 13 51 21" src="https://user-images.githubusercontent.com/118350020/207600192-a5633d00-f463-4222-badf-f065c8148dfa.png">

 
The next piece of our application will be the MongoDB Database.

