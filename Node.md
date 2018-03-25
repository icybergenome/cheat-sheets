## Basics ##
* Chrome's v8 JS engine is built using C++.
* Using V8 engine it gives ability to JS to perform tasks that it otherwise couldn't do. Such as:
  * read, write or delete data from DB.
  * Generate dynamic page content(Node)
  * Node.js can create, open, read, write, delete, and close files on the server
* NodeJS is asynchronous, nonblocking and single-threaded meaning:
  * Unlike other langs or framework it doesn't wait for a request to complete before it could perform another request(asynchronous). Delete that request from queue and jump to the next one.
  * Its like a middleman which could help JS do cool stuff using power of C++.

## Global Object ##
* **Window** in browser is **global** in Node.
* Unlike browser side JS where every declaration of variable with keyword var is global. So in node we can't access variable like **global.varName**.
* In Node each file is a separate module so it requires export and import of attributes to access.

### Node Functionality basic ###
* All browser side JS functionalities are available in NodeJS also.
* Node could also be able to access local directory and current file info (i.e. `__`dirname and `__`filename).

## Process Object ##
Provides is a global object that provides information about, and control over, the current Node.js process.

>process.stdout.write('Ask me a question now');
>
process.stdin.on('data', function(answer){
>
    console.log(answer.toString().trim());
>
    process.exit();
>
});

## Readline Object ##
A wrapper over Process object which provides more easy and enhanced input and output functions.

>var readline = require('readline');
>
var util = require('util');
>
var RL = readline.createInterface(process.stdin, process.stdout);
>
RL.question('What is your name? ', (name)=>{
>
    RL.setPrompt(`${name} how old are you? `);
>
    RL.prompt();
>
    RL.on('line', (age)=>{
>
        if(age < 18){
>
            util.log(`${name.trim()} because you are ${age} years old, you cannot proceed`);
            RL.close();
>
        }else {
>
            util.log(`${name.trim()} is great that you are ${age} years old, because now you can enjoy our services`);
            RL.close();
        }
>
    });
>
});

## Custom Events and Exports ##
Modules could be exported and imported on other end.

>const events = require('events');
>
let emitter = new events.EventEmitter();
module.exports = emitter;

>const events = require('events');
>
let emitter = new events.EventEmitter();
>
emitter.on('newEvent', (message)=>{
>
   console.log(`Message: ${message}`);
>
});
>
emitter.emit('newEvent', 'Hello guys this is Edwin Diaz');

## Child Process ##
>const execute = require('child_process').exec;
>
execute("ls", (err, stdout)=>{
>
    if(err){
>
        return err;
>
    }
>
    console.log(stdout);
});

## Read File ##
>const fs = require('fs');
>
fs.readdir('./', (err, content)=>{
>
    if(err) return err;
>
    console.log(content);
>
});
>
fs.readFile('global.html', 'UTF-8', (err, content)=>{
>
    console.log(content);
>
});

## Creating Server ##
We can create a server which will use http built in module of node.

## Axios ##
Third part library which makes receiving request and callback more easier.

>const axios = require('axios');
>
let username = 'icybergenome';
>
axios.get('https://api.github.com/users/' + username).then((res)=>{
>
    console.log(res.data);
>
}).catch((err)=>{
>
    console.log(err);
>    
});

##Nodemon##
* To automate the process of server restarting on changes in a code file and detecting the change we use nodemon package (i.e. `npm install nodemon`).

#Express#
-ExpressJS is a framework/library which is to assist node for a more simpler code with less lines.
-For APIs or routes to access data we could use node but with express it lot easier.

##Middleware##
-It is some sort of functionality that we plugin to our app before the request and response is received.

>const express = require('express');
>
let app = express();
app.use('/css', express.static(__dirname__ + '/public'));
>
app.use((req, res, next) =>{
>
    console.log('MIDDLEWARE');
>
    next();
>
});
>
app.get('/', (req, res)=>{
>
   res.send(`   
    <!doctype html>
<html lang="en">
<head>
>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="/css/style.css">
    <title>Document</title>`


`</head>`
>`<body>`
>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit.
    </p>
>
> `</body>`
> `</html>`
>
  `);`

>});

>app.listen(9999);
>
console.log(`It's working`);


* express static function will serve the required files statically. Behind the scene it will read the file and provide the data in required format.
* Based on path provided our MIDDLEWARE can serve a required functionality.
* **next()** function allows to server to receive next request.

##NPM repository##
Most widely used repository with tons of packages available. Common commands are:

CMD | Purpose
----|---------
npm init | instantiate node project to specify dependencies.
npm install [pkg] | Install package
npm update | update the node package according to changes in *package.json*
npm outdated| figure out outdated packages
npm run [cmd] | run command specified in *package.json*
Flag: -g | install globally
Flag: --save | list in dependency list, no longer required in latest node.
Flag: --save-dev | list in dev dependency list.

##Body Parser##
* Express does not by default support parsing post data. So we use third party package named Body Parser. `npm install body-parser`.

##Http Verbs##
Any of the verb lets say **Get** could be used to perform any task by other verbs but as per best practises functionalities of each verb as follow:
* Get to fetch data.
* Post to create or insert data.
* Put to update data, but we need to specify all the field in our model requires by a schema. Usually put is used to replace all the data.
* Patch to update data, to update a specific data or field.
