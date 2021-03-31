# avgayoma_tier1

HOST=dbhosturl
USERNAME=dbusername
PASSWORD=itsyourday
DATABASE=dbname

node_modules 
node_modules
.env 

  "homepage": "https://github.com/w3dotmakinadotnull/express-minimal-app#readme",
  "dependencies": {
    "cors": "^2.8.5",
    "dotenv": "^8.2.0",
    "express": "^4.17.1",
    "helmet": "^4.1.1",
    "morgan": "^1.10.0"
    "morgan": "^1.10.0",
    "mysql": "^2.18.1"
  },
  "devDependencies": {
    "eslint": "^7.9.0",
    
require('dotenv').config()
const express = require('express')
const morgan = require('morgan')
// const helmet = require('helmet')
const cors = require('cors')
const mysql = require('mysql')

const middlewares = require('./middlewares')

const app = express()
app.use(morgan('common'))
// app.use(helmet())
app.use(cors())

app.get('/', (req, res) => {
@@ -27,6 +27,30 @@ app.use(middlewares.errorHandler)

const port = process.env.PORT || 1337

const {
  HOST,
  USERNAME,
  PASSWORD,
  DATABASE
} = process.env

app.listen(port, () => {
  console.log(`Server running: Listening at https://localhost:${port}`)
  // DON'T EDIT or MODIFY!!!!
  const connection = mysql.createConnection({
    host: HOST,
    user: USERNAME,
    password: PASSWORD,
    database: DATABASE
  })

  connection.connect();

  connection.query('SELECT 1 + 1 AS solution', function (error, results, fields) {
    if (error) throw error;
    console.log('The solution is: ', results[0].solution);
    console.log('Database is operating normally')
    console.log(`Server running: Listening at http://localhost:${port}`)
  });

  connection.end();
