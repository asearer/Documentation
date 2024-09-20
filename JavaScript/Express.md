### Guide to Using Express.js

Express.js is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications. This guide will walk you through the basics of setting up and using Express.js.

#### 1. Prerequisites
Before diving into Express.js, ensure you have a solid understanding of:
- JavaScript (ES6+ features)
- Node.js and npm (Node Package Manager)

#### 2. Setting Up the Development Environment
Ensure Node.js and npm are installed. You can download them from [nodejs.org](https://nodejs.org/).

Check installation:
```bash
node -v
npm -v
```

#### 3. Creating a New Express.js Project
To create a new Express.js project, you can use the following steps:

1. Create a new directory for your project:
```bash
mkdir my-express-app
cd my-express-app
```

2. Initialize a new Node.js project:
```bash
npm init -y
```

3. Install Express.js:
```bash
npm install express
```

#### 4. Basic Express Server Setup
Create an entry point file (e.g., `index.js`) and set up a basic Express server:

```javascript
// index.js
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello, Express!');
});

app.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});
```

Start the server:
```bash
node index.js
```

#### 5. Middleware
Middleware functions are functions that have access to the request object (`req`), the response object (`res`), and the next middleware function in the application’s request-response cycle.

Example of using middleware:
```javascript
const express = require('express');
const app = express();
const port = 3000;

app.use((req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
});

app.get('/', (req, res) => {
  res.send('Hello, Express with Middleware!');
});

app.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});
```

#### 6. Routing
Express makes it easy to define routes for your application.

Basic routing example:
```javascript
app.get('/about', (req, res) => {
  res.send('About Page');
});

app.post('/submit', (req, res) => {
  res.send('Form Submitted');
});
```

#### 7. Static Files
To serve static files such as images, CSS files, and JavaScript files, use the `express.static` built-in middleware function.

Example:
```javascript
app.use(express.static('public'));
```
Now, you can access files in the `public` directory.

#### 8. Handling Form Data
To handle form data, use the `express.urlencoded` middleware.

Example:
```javascript
app.use(express.urlencoded({ extended: true }));

app.post('/submit', (req, res) => {
  res.send(`Form Submitted. Name: ${req.body.name}`);
});
```

#### 9. JSON Data
To handle JSON data, use the `express.json` middleware.

Example:
```javascript
app.use(express.json());

app.post('/api/data', (req, res) => {
  res.json({ received: req.body });
});
```

#### 10. Templating Engines
Express supports various templating engines like Pug, EJS, and Handlebars.

Example using Pug:
1. Install Pug:
```bash
npm install pug
```

2. Set Pug as the templating engine:
```javascript
app.set('view engine', 'pug');
app.set('views', './views');

app.get('/', (req, res) => {
  res.render('index', { title: 'Hey', message: 'Hello there!' });
});
```

Create a `views/index.pug` file:
```pug
html
  head
    title= title
  body
    h1= message
```

#### 11. Express Router
The `express.Router` class can be used to create modular, mountable route handlers.

Example:
```javascript
const express = require('express');
const app = express();
const port = 3000;
const router = express.Router();

router.get('/user/:id', (req, res) => {
  res.send(`User ID: ${req.params.id}`);
});

app.use('/api', router);

app.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});
```

#### 12. Error Handling
Express provides a simple way to handle errors.

Example:
```javascript
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```

#### 13. Connecting to a Database
Express can be used with various databases. Here’s an example using MongoDB with Mongoose:

1. Install Mongoose:
```bash
npm install mongoose
```

2. Connect to MongoDB and define a model:
```javascript
const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost:27017/myapp', { useNewUrlParser: true, useUnifiedTopology: true });

const User = mongoose.model('User', { name: String });

app.get('/add-user', async (req, res) => {
  const user = new User({ name: 'John Doe' });
  await user.save();
  res.send('User added');
});
```

#### 14. Session Management
For session management, you can use `express-session`.

1. Install `express-session`:
```bash
npm install express-session
```

2. Use the session middleware:
```javascript
const session = require('express-session');

app.use(session({
  secret: 'your secret key',
  resave: false,
  saveUninitialized: true,
}));

app.get('/', (req, res) => {
  if (req.session.views) {
    req.session.views++;
    res.send(`Number of views: ${req.session.views}`);
  } else {
    req.session.views = 1;
    res.send('Welcome to the session demo. Refresh!');
  }
});
```

#### 15. Authentication
For authentication, you can use Passport.js.

1. Install Passport.js and related modules:
```bash
npm install passport passport-local express-session
```

2. Configure Passport.js:
```javascript
const passport = require('passport');
const LocalStrategy = require('passport-local').Strategy;

passport.use(new LocalStrategy((username, password, done) => {
  // Here you would lookup the user in your DB and compare the password
  if (username === 'user' && password === 'pass') {
    return done(null, { id: 1, name: 'John Doe' });
  } else {
    return done(null, false, { message: 'Incorrect username or password.' });
  }
}));

passport.serializeUser((user, done) => {
  done(null, user.id);
});

passport.deserializeUser((id, done) => {
  done(null, { id, name: 'John Doe' });
});

app.use(session({
  secret: 'your secret key',
  resave: false,
  saveUninitialized: true,
}));
app.use(passport.initialize());
app.use(passport.session());

app.post('/login', passport.authenticate('local', {
  successRedirect: '/dashboard',
  failureRedirect: '/login',
}));

app.get('/dashboard', (req, res) => {
  if (req.isAuthenticated()) {
    res.send(`Hello ${req.user.name}`);
  } else {
    res.redirect('/login');
  }
});
```

#### 16. Logging
To log requests, you can use `morgan`.

1. Install `morgan`:
```bash
npm install morgan
```

2. Use the morgan middleware:
```javascript
const morgan = require('morgan');

app.use(morgan('dev'));
```

#### 17. Deployment
To deploy your Express application, you can use services like Heroku, Vercel, or your own server.

Example deployment to Heroku:
1. Install the Heroku CLI and log in:
```bash
npm install -g heroku
heroku login
```

2. Create a `Procfile` in the root of your project:
```txt
web: node index.js
```

3. Initialize a git repository, commit your code, and push to Heroku:
```bash
git init
heroku create
git add .
git commit -m "Initial commit"
git push heroku master
```

4. Open your application:
```bash
heroku open
```

#### 18. Best Practices
- Use environment variables for configuration (e.g., using `dotenv`).
- Structure your project with a clear and consistent folder structure.
- Use middleware for common functionality (logging, authentication, etc.).
- Handle errors gracefully.
- Write tests for your application.
- Secure your application (e.g., using Helmet).

#### 19. Useful Resources
- [Express.js Official Documentation](https://expressjs.com/)
- [Node.js Official Documentation](https://nodejs.org/en/docs/)
- [Express.js Guide](https://expressjs.com/en/guide/routing.html)
- [Mozilla Developer Network (MDN) - Express Tutorial](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs)
- [The Modern JavaScript Tutorial](https://javascript.info/)
- [Passport.js Documentation](http://www.passportjs.org/docs/)
- [Mongoose Documentation](https://mongoosejs.com/docs/)

