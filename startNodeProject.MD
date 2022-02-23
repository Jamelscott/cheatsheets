# Setting up a Node.js project

- npm i -g [modulename]  (Only done once - installs modules globally)
- start a new folder
- sudo npm init -y (install and skip)
- touch .gitignore (in that file type in 'node_modules')
- create an index.js file (entry point)
- code . into your file
- run nodemon in the console for a live feed of js console

## See below if you're creating your own module
- create a module.js file
- link the modele.js to index.js via a variable in index.js
- example: const myModule = require('./module.js')

## See below if you're using a NPM module package
- npm i [modulename] (installs modules locally)

### Example:
        npm i express ejs express-ejs-layouts

## See below if you're installing Express
- npm i express (if you haven't already)
- in your index file, here is the setup

### import express setup:
         const express = require('express')
         const app = express();
         app.listen(8000, ()=>{
         console.log("port 8000 is open for business")

- set up first view and test that the client can view it

         app.get('/', (req, res)=>{
         res.send("Hello,  World!")
         })

- this will act as your home page since the URL is only the base.

## See below if you're installing EJS
- npm i ejs
- npm i express-ejs-layouts (if layouts are required)
- create 'views' directory
- create a index.ejs file in that directory(your home page)
- in your index.js add middlewere to express:

### import EJS middlewere setup:
- this goes at the top with the other requires:

            const ejsLayouts = require('express-ejs-layouts');

- this is the middlewere:
 
            app.set('view engine', 'ejs')
            app.use(ejsLayouts)

- create a layout.ejs file in the views directory
- setup an HTML boilerplate in layout.ejs including the body gateway:
    - add a header so you will be able to troubleshoot later.

### Insert the template EJS layout HTML boilerplate:
                    <!DOCTYPE html>
            <html lang="en">
            <head>
                <meta charset="UTF-8">
                <meta http-equiv="X-UA-Compatible" content="IE=edge">
                <meta name="viewport" content="width=device-width, initial-scale=1.0">
                <title>Document</title>
            </head>
            <body>
                <%- body %>
            </body>
            </html>

- add some HTML to the index.ejs file (ex. <h1> )
- check if view files are working by routing to index.ejs

        app.get('/', (req, res) => {
        res.render('index');
        });

- if you see the HTML from the layout.ejs and underneither HTML from index.ejs, you have successfully connected them.


## Controllers
- design how you would like to group your routes
- create a controllers folder

- create a .js file that will hold multiple routes
- connect your controller to express:
const express = require('express');
const router = express.Router();
- at the bottom of your page, include:
module.exports = router;
-in between the express link and module.exports include your routes:
    - those route use the same syntax as in your index.js but you need to change app.get to router.get
- in your index.js file, you need to link your controller files.
//app.use('/url-to-prefix-all-the-routes-with', theControllerFile)
exmaple: app.use('/love-it', require('./controllers/loveItControllers.js'))
- you will need one of these for each controller file you create.
- ** this file must be under all of your middlware **


# TLDR; 
- sudo npm init -y (install and skip)
- touch .gitignore (in that file type in 'node_modules') so node_modles isn't uploaded to github
- create an index.js file (entry point)
- install npm packages 
- - npm i express ejs express-ejs-layouts
- copy/paste this into terminal to have nodemon reset when saving ejs files
nodemon --exec node index.js -e .js,.json,.ejs
- Open index.js and create a variable to link the express NPM: 
const express = require('express')
- create a variable that runs the express NPM
const app = express();
- create a port number variable (not necessary but good practice)
const port = 8000;
- setup the port (keep this at the bottom of your js file)
app.listen(port, ()=>{
    console.log("easy listening from ${port}🎙)
})
- the server by running nodemon in the terminal
- setup a port route
app.get('/', (req, res)=>{
    res.send("Hello, World!")
})
- in a client, open localhost:8000;
- if you are seeing hello world, your server is setup properly
If all is good continue..
- create a views folder
- create a layout.ejs and index.ejs file in that folder
- in index.js rename the 

# How to access form data via req.body; 
-- add middleware
app.use(express.urlencoded({extended: false}))
-- body.req to access information in forms

# How to update data from a local json file
- install method-override (npm i method-override)
- import into index.js - const methodOverride = require('method-override')
- add middleware into index.js - app.use(methodOverride('_method'))
- if you need to read the file then parse it into JS
example:  let prehistoricCreatures = fs.readFileSync('./prehistoric_creatures.json')
- if you need to write the file then parse it into JS
example:   fs.writeFileSync('./prehistoric_creatures.json', JSON.stringify(creaturesData))




# Tips!
- if youre having trouble with other open ports
    - use killall node as a hard reset.
- add this to your script if you want nodemon to refresh when a ejs file is saved
    - "start": "nodemon --exec node index.js -e .js,.ejs,.json"

