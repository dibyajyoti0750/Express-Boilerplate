## Setting Up an Express Boilerplate

Follow these steps to set up a basic Express.js boilerplate with EJS as the templating engine and static file support.

#### 1. Initialize the Project

`$ npm init -y`

#### 2. Install Required Packages

`$ npm install express ejs`

#### 3. Create the Main Server File

Create a new file named index.js and add the following code:

```
const express = require("express");
const path = require("path");

const app = express();
const port = 8080;

app.use(express.urlencoded({ extended: true }));
app.use(express.json());

app.set("view engine", "ejs");
app.set("views", path.join(__dirname, "views"));

app.use(express.static(path.join(__dirname, "public")));

app.get("/", (req, res) => {
res.render("home");
});

app.listen(port, () => {
console.log(`Server running at http://localhost:${port}`);
});
```

#### 4. Create Required Directories

`$ mkdir -p views/includes public/css public/js`

✅ This creates:

views/ → Contains template files.

views/includes/ → Stores reusable partials like headers and footers.

public/css/ → Stores CSS files.

public/js/ → Stores JavaScript files.

#### 5. Create the Home View

Inside views/ create a file named `home.ejs` and add:

```
<%- include("includes/header.ejs", {title:"Home"}) %>
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

#### 6. Create the Header and Footer Includes

Inside views/includes/ create `header.ejs`:

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title><%= title %></title>
    <link rel="stylesheet" href="/styles.css" />
  </head>
</html>
```

Inside views/includes/ `create footer.ejs`

#### 7. Create Static Files

➤ Create the CSS File
Inside public/css/ create `styles.css` and add:

```
body {
font-family: Arial, sans-serif;
text-align: center;
padding: 20px;
}
```

➤ Create the JavaScript File
Inside public/js/ create `app.js` and add:

```
console.log("JavaScript loaded successfully!");
```

#### 8. Run the Server with Nodemon

Install nodemon globally if not already installed:

`$ npm install -g nodemon`

`$ nodemon index.js`

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
