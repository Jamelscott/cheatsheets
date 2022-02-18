<!-- Steps for starting a node project -->
- npm i -g [modulename](Only done once - installs modules globally)
- start a new folder
- sudo npm init -y (install and skip)
- create an index.js file (entry point)
- touch .gitignore (in that file type in 'node_modules')

<!-- - - - if using your own module - - -  -->
- create a module.js file
- link the modele.js to index.js via a variable in index.js
- example: const myModule = require('./module.js')

<!-- - - - if using NPM module package - - -  -->
- npm i [modulename] (installs modules locally)
        
        <!-- the typical -->
        - npm i express ejs express-ejs-layouts

- touch .gitignore (if not being used in a repo)
- run nodemon in the console for a live feed of js console


<!-- - - - if installing Express - - - -->
- npm i express (if you haven't already)
- in your index file, here is the setup

        <!-- import express setup -->
        const express = require('express')
        const app = express();
        app.listen(8000, ()=>{
        console.log("port 8000 is open for business")

- set up first view and test that the client can view it

        app.get('/', (req, res)=>{
        res.send("Hello,  World!")
        })

- this will act as your home page since the URL is only the base.

<!-- - - - if installing EJS - - -  -->
- npm i ejs
- npm i express-ejs-layouts (if layouts are required)
- create 'views' directory
- create a index.ejs file in that directory(your home page)
- in your index.js add middlewere to express:

        <!-- import EJS middlewere setup -->

        // this goes at the top with the other requires //
            const ejsLayouts = require('express-ejs-layouts');

        //this is the middlewere //
            app.set('view engine', 'ejs')
            app.use(ejsLayouts)

- create a layout.ejs file in the views directory
- setup an HTML boilerplate in layout.ejs including the body gateway:
    - add a header so you will be able to troubleshoot later.

            <!-- template EJS layout HTML boilerplate -->
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

