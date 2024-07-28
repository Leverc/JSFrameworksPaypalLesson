# JSFrameworksPaypalLesson
 Lesson Code and Instructions for JS Frameworks Paypal lecture

## Step 1: Scaffolding a Node.js Project

### 1. Install Node.js and npm
Download and install Node.js and npm from [nodejs.org](https://nodejs.org/).

### 2. Create a Project Directory
```sh
mkdir my-node-project
cd my-node-project
```
### 3. Initialize the Project
```sh
Copy code
npm init -y
```
### 4. Install Essential Packages
```sh
Copy code
npm install express
```
### 5. Set Up the Project Structure
```sh
Copy code
mkdir src
touch src/index.js
```
### 6. Create a Simple Express Server
```sh
Add the following code to src/index.js:

js
Copy code
const express = require('express');
const app = express();
const PORT = process.env.PORT || 3000;

app.get('/', (req, res) => {
  res.send('Hello, World!');
});

app.listen(PORT, () => {
  console.log(`Server is running on http://localhost:${PORT}`);
});
```
### 7. Add Scripts to package.json
```sh
Add a start script:

json
Copy code
"scripts": {
  "start": "node src/index.js"
}
```
### 8. Run the Project
```sh
Copy code
npm start
Project Structure
go
Copy code
my-node-project/
├── node_modules/
├── src/
│   └── index.js
├── package.json
└── package-lock.json
This sets up a basic Node.js project with an Express server.
```
## Step 2: Setting Up a PayPal Account

### 1. Creating a PayPal Account
- Go to [PayPal's website](https://www.paypal.com/).
- Click on the "Sign Up" button.
- Choose "Personal Account".
- Follow the on-screen instructions to complete the sign-up process.

## Step 3: Adding a PayPal Buy Now Button

### 1. Generating the PayPal Buy Now Button
1. Log in to your PayPal account.
2. Navigate to the settings by clicking the cog in the top right.
3. Click on "Seller Tools".
4. In the "All Tools" section, select "PayPal Buttons".
5. Choose the "Buy Now" button option.
6. Customize your button:
   - **Item Name**: Enter the name of the item you are selling.
   - **Item ID**: Optional, for your tracking purposes.
   - **Price**: Set the price for your item.
   - **Currency**: Choose your preferred currency.
   - **Button Style**: Customize the appearance of your Buy Now button.
7. Click "Create Button".

### 2. Getting the HTML Code
- After customizing the button, PayPal will generate HTML code for you.
- Copy this HTML code for use on your website.

## Step 4: Adding the Button to Your node.js Project

### 1. Add file structure
1. Create a new folder at the root level labelled "views"

### 2. Create index.html file
1. Inside the new "views" folder create a new file named "index.html"
2. Add the following html to scaffold a basic page:
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Buy Now</title>
  </head>
  <body>
    <h1>Buy Our Product</h1>

  </body>
</html>
```
3. Under the "h1" tag add the html provided from paypal

### 3. Serve index.html Using Our index.js File
1. Change your index.js to serve the index.html, here is an example:
```sh
const express = require('express');
const path = require('path');
const app = express();
const PORT = process.env.PORT || 3000;

// Serve static files from the "views" directory
app.use(express.static(path.join(__dirname, '../views')));

app.get('/', (req, res) => {
  res.sendFile(path.join(__dirname, '../views/index.html'));
});

app.listen(PORT, () => {
  console.log(`Server is running on http://localhost:${PORT}`);
});
```






