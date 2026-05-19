# Admin Panel Project

A simple Node.js + Express admin panel project with authentication, session handling, MongoDB integration, Passport.js login system, EJS templates, and CRUD functionality.

## Passport Authentication

This project uses Passport.js for admin authentication.

### Passport.js Features Used

* Local Strategy Authentication
* Login Authentication
* Session Management
* Serialize User
* Deserialize User
* Protected Routes

### Passport Configuration Example

```js
const passport = require('passport');
const LocalStrategy = require('passport-local').Strategy;
const Admin = require('../models/adminModel');

passport.use(new LocalStrategy({
    usernameField: 'email'
}, async (email, password, done) => {
    const user = await Admin.findOne({ email });

    if (!user) {
        return done(null, false);
    }

    if (user.password !== password) {
        return done(null, false);
    }

    return done(null, user);
}));

passport.serializeUser((user, done) => {
    done(null, user.id);
});

passport.deserializeUser(async (id, done) => {
    const user = await Admin.findById(id);
    done(null, user);
});
```

### Required Passport Packages

```bash
npm install passport passport-local express-session
```

### Passport Middleware Setup

```js
app.use(session({
    secret: 'adminpanel',
    resave: false,
    saveUninitialized: false
}));

app.use(passport.initialize());
app.use(passport.session());
```

## Features

* Admin authentication using Passport.js
* Session management with Express Session
* MongoDB database connection using Mongoose
* EJS templating engine
* File upload support using Multer
* Admin dashboard
* Add / Edit / Delete admin data
* Static public assets support

## Tech Stack

* Node.js
* Express.js
* MongoDB
* Mongoose
* Passport.js
* EJS
* Multer
* Express Session

## Project Structure

```bash
admin-paln-cookie-Copy1-passport-fixed/
│
├── app.js
├── package.json
├── config/
│   ├── db.js
│   └── passport.js
│
├── controllers/
├── middleware/
├── models/
├── router/
├── views/
├── public/
└── node_modules/
```

## Installation

### 1. Clone the project

```bash
git clone <repository-url>
```

### 2. Open project folder

```bash
cd admin-paln-cookie-Copy1-passport-fixed
```

### 3. Install dependencies

```bash
npm install
```

### 4. Install MongoDB package

```bash
npm install mongoose
```

## MongoDB Setup

Make sure MongoDB is installed and running locally.

Default local MongoDB URL:

```bash
mongodb://127.0.0.1:27017/adminpanel
```

Update your database connection inside:

```bash
config/db.js
```

Example:

```js
const mongoose = require('mongoose');

mongoose.connect('mongodb://127.0.0.1:27017/adminpanel')
.then(() => console.log('successfully connected'))
.catch((err) => console.log(err));
```

## Run Project

Start the server:

```bash
npm start
```

or

```bash
node app.js
```

## Server

Project runs on:

```bash
http://localhost:9000
```

## Dependencies

Main packages used in this project:

```json
{
  "bcrypt": "^6.0.0",
  "cookie-parser": "^1.4.7",
  "ejs": "^5.0.2",
  "express": "^5.2.1",
  "express-session": "^1.19.0",
  "mongoose": "^9.6.2",
  "multer": "^2.1.1",
  "passport": "^0.7.0",
  "passport-local": "^1.0.0"
}
```

## Common Errors

### Cannot find module 'app.js'

Make sure you are inside the correct project folder:

```bash
cd admin-paln-cookie-Copy1-passport-fixed
```

Then run:

```bash
npm start
```

### MongoDB Connection Error

* Check if MongoDB service is running
* Verify database URL in `config/db.js`
* Reinstall mongoose if needed

```bash
npm install mongoose
```

### Port Already In Use

Change the port inside `app.js`

```js
const port = 9000;
```

## Author

Admin Panel Project
<img width="1903" height="887" alt="Screenshot pass3" src="https://github.com/user-attachments/assets/71e4467a-aedd-4e75-9b9b-6f52d336c6ac" />
<img width="1903" height="887" alt="Screenshot pass3" src="https://github.com/user-attachments/assets/f6d0e611-2be1-4f05-b30a-ec641cf3cd81" />
<img width="1907" height="966" alt="Screenshot pass1" src="https://github.com/user-attachments/assets/b3147cd6-84ec-4cd5-87eb-41e9227d4a5c" />
<img width="1908" height="968" alt="AdobeExpressPhotos_a10cb8faba764b9c93a59caa69e595db_CopyEdited" src="https://github.com/user-attachments/assets/6c24f6ec-26f4-40e3-94d1-72552d68ff84" />
