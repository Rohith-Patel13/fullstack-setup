>create fullstack-projectName folder name in  vs code terminal by using below command:
 ```bash
 mkdir fullstack-projectName
 ```

>create client and server folder in fullstack-projectName by using below commands:
```bash
 mkdir client
 ```

 ```bash
 mkdir server
 ```

>navigate to client folder and run below command:
  ```bash
  npx create-react-app .
  ```

>open package.json file in client folder and add "proxy":"http://localhost:portNumber/", as below example:
```json
  {
  "name": "client",
  "version": "0.1.0",
  "proxy":"http://localhost:8385/",
  "private": true,
  "dependencies": {
    "@testing-library/jest-dom": "^5.17.0",
    "@testing-library/react": "^13.4.0",
    "@testing-library/user-event": "^13.5.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-scripts": "5.0.1",
    "web-vitals": "^2.1.4"
  },
  ....,
  ....,
  }
```


>delete all unnecessary images like logo.svg in public and src folders on client folder 

>navigate to server folder create below files by using following commands:
 ```bash
 touch projectName.js
 ```
 ```bash
 touch .gitignore
 ```
 ```bash
 touch projectName.db
 ```

>open .gitignore file and write below line in that  file:
  node_modules/


>open projectName.js file and write below exampled prefilled code and change database name(projectName.db) and port number(8385,8386 as same as client side proxy):
```javascript
const express = require("express");
const path = require("path");
const { open } = require("sqlite");
const sqlite3 = require("sqlite3");

//const { format } = require("date-fns");

const app = express();
const cors = require('cors');
app.use(cors()); // Enable CORS for all routes
app.use(express.json());

// const jwt = require("jsonwebtoken");
// const bcrypt = require("bcrypt");


const dbPath = path.join(__dirname, "shopping.db");
let dbConnectionObject = null;
const initializeDBAndServer = async () => {
  try {
    dbConnectionObject = await open({
      filename: dbPath,
      driver: sqlite3.Database,
    });
    app.listen(8385, () => {
      console.log("Server Running at http://localhost:8385/");
    });
  } catch (e) {
    console.log(`DB Error: ${e.message}`);
    process.exit(1);
  }
};
initializeDBAndServer();

```


>open new terminal and open gitbash and run below command in server folder:
  ```bash
  npm install bcrypt cors date-fns express jsonwebtoken sqlite sqlite3 --save
  ```

>open package.json file in and add   "start": "node server","dev": "nodemon server" in scripts object as below in server folder:
 ```json
  {
  "name": "server",
  "version": "1.0.0",
  "description": "",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node server",
    "dev": "nodemon server"
  },
  "keywords": [],
  ....,
  ....,

 ```

>after completion of project upload it in github and below commands are for reference:
# git-commands
```bash
   git init 
   git add -A 
   git commit -m “commit message” 
   git remote add origin <repository-url>
   git branch -M main 
   git push -u origin main 
```  

After changing any file continuation commands for above:
```bash
git add changed_content_file_name
```
```bash
git commit -m “changed_content_file_name  commit message”
```
```bash
git push -u origin main
```

for removing origin
```bash
git remote rm origin 
```

for removing ./git folder
```bash
rm -rf .git 
```


>## Database Interaction
To manage the SQLite database used in this project, you can use the SQLite command-line tool. In the `server` directory, you'll find a prepopulated database file named `projectName.db`. Below are some useful commands to interact with the database:

### Open SQLite Command-Line Tool
To open the SQLite command-line tool, navigate to the `server` directory and run the following command:
```bash
sqlite3 projectName.db
```

**View Tables in the Database**
To view the list of tables in the database, use the following command within the SQLite command-line tool:
```sql
.tables
```

**Retrieve All Data in the "tasks" Table**
To retrieve all data from the tasks table, execute the following SQL query:
```sql
SELECT * FROM projectNameTable;
```

**View Table Schema**
To view the schema of the tasks table, including the column details, use the following command:
```sql
PRAGMA table_info(projectNameTable);
```

**Exit SQLite Command-Line Tool**
To exit from the SQLite command-line tool, simply enter the following command:
```sql
.exit
```



## How to Run the Application

Follow these steps to run the to-do list web application on your local machine:

### Step 1: Clone the Repository
First, clone the repository to your local machine in VS Code using Git:
```bash
git clone <repository_url>
```

**Step 2: Set Up the Back-End**
Open your terminal and navigate to the server directory using the following commands:
```bash
cd server
```
Next, install the back-end dependencies and start the application:
```bash
npm install
```
```bash
npm run dev
```

**Step 3: Set Up the Front-End**
In a new terminal window (you can split the terminal with Ctrl+Shift+5), navigate to the client directory:
```bash
cd client
```

Install the front-end dependencies:
```bash
npm install
```

Start the front-end server:
```bash
npm start
```



**Step 4: Access the Application**
Now, you can access the to-do list web application by opening a web browser and going to
http://localhost:3000/
   
 
 