1) *npm init* to create a new npm project in a named folder
2) *npm i express body-parser mongoose concurrently*
   1) express - server framework
   2) body-parser for handling reponse/request body
   3) mongoose - database
   4) concurrently - to run server and client concurrently
3) *npm i -D nodemon* to add node monitoring in dev environment for any new changes
4) modify the scripts in package.json to add scripts for *start* and *server* 
5) create server.js (import all dependencies)
6) User mlab or local mongodb for database. mlab is good option for dev projects.
7) Create cluster on a clound provider and create database/collection and get connection URI
8) Create a config folder and keys.js file to store config details such as Mongo URI
9) Import the config to server.js and connect to db using js promise capturing results
10) configure the server to listen on a specified port.
11) do *npm run server*  (based on script added step 4) to see the server started and connected to db.
12) create models folder for data model and add js files for each database model
13) add routes folder and items.js to address each api request (GET/POST/DELETE) - see item.js
14) 