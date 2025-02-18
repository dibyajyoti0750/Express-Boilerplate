## Setting Up an Express Boilerplate

Follow these steps to set up a basic Express.js boilerplate with EJS as the templating engine and static file support.

#### 1️⃣ Initialize the Project

`bash`
`npm init -y`

#### 2️⃣ Install Required Packages

npm install express ejs

#### 3️⃣ Create the Main Server File

Create a new file named index.js and add the following code:

```const express = require("express");
const path = require("path");

const app = express();
const port = 8080;

// Set EJS as the templating engine
app.set("view engine", "ejs");
app.set("views", path.join(\_\_dirname, "views"));

// Serve static files
app.use(express.static(path.join(\_\_dirname, "public")));

// Home route
app.get("/", (req, res) => {
res.render("home");
});

// Start the server
app.listen(port, () => {
console.log(`Server running at http://localhost:${port}`);
});
```

#### 4️⃣ Create Required Directories

mkdir -p views/includes public/css public/js

✅ This creates:

views/ → Contains template files
views/includes/ → Stores reusable partials like headers and footers
public/css/ → Stores CSS files
public/js/ → Stores JavaScript files

#### 5️⃣ Create the Home View

Inside views/, create a file named home.ejs and add:

```<%- include("includes/header.ejs") %>

<body>
  <h1>Welcome Home</h1>
  <p>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Corporis delectus,
    quisquam, reprehenderit deserunt facere incidunt, dolore adipisci non
    numquam dolor explicabo dolorem doloremque laborum officia qui tenetur sunt
    itaque animi?
  </p>
  <%- include("includes/footer.ejs") %>
  <script src="/js/app.js"></script>
</body>
```

#### 6️⃣ Create the Header and Footer Includes

Inside views/includes/, create header.ejs:

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Express Boilerplate</title>
    <link rel="stylesheet" href="/css/styles.css" />
  </head>
  <body></body>
</html>

Inside views/includes/, create footer.ejs

#### 7️⃣ Create Static Files

➤ Create the CSS File
Inside public/css/, create styles.css and add:

body {
font-family: Arial, sans-serif;
text-align: center;
padding: 20px;
}

➤ Create the JavaScript File
Inside public/js/, create app.js and add:

console.log("JavaScript loaded successfully!");

#### 8️⃣ Run the Server with Nodemon

Install nodemon globally if not already installed:

npm install -g nodemon

nodemon index.js

✅ The server will start at http://localhost:8080/

#### 🎯 Project Overview

```/project-folder
│── index.js
│── package.json
│── /views
│   ├── home.ejs
│   ├── /includes
│   │   ├── header.ejs
│   │   ├── footer.ejs
│── /public
│   ├── /css
│   │   ├── styles.css
│   ├── /js
│   │   ├── app.js
```
