# Guide to Using Node.js

Node.js is a powerful, event-driven, non-blocking I/O platform built on Google Chrome's V8 JavaScript engine. It's widely used for building scalable network applications. This guide will cover the basics and some advanced topics to help you get started with Node.js.

## 1. Prerequisites

Before diving into Node.js, ensure you have a solid understanding of:

- JavaScript (ES6+ features)
- Basic terminal/command prompt usage

## 2. Setting Up the Development Environment

Ensure Node.js and npm (Node Package Manager) are installed. You can download them from [nodejs.org](https://nodejs.org).

Check installation:

```bash
node -v
npm -v
```

## 3. Creating a New Node.js Project

To create a new Node.js project, you can use the following steps:

Create a new directory for your project:

```bash
mkdir my-node-app
cd my-node-app
```

Initialize a new Node.js project:

```bash
npm init -y
```

This will generate a `package.json` file with default settings.

## 4. Basic Node.js Server

Create an entry point file (e.g., `index.js`) and set up a basic HTTP server:

```javascript
// index.js
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello, Node.js!\n');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

Start the server:

```bash
node index.js
```

## 5. Understanding Node.js Modules

Node.js has a modular architecture and uses modules to manage code. You can use built-in modules or create your own.

Example of using a built-in module (`fs` for file system operations):

```javascript
const fs = require('fs');

fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});
```

## 6. Creating Custom Modules

You can create custom modules and export functions, objects, or values.

Example of a custom module (`math.js`):

```javascript
// math.js
function add(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}

module.exports = { add, subtract };
```

Using the custom module in another file:

```javascript
// index.js
const math = require('./math');

console.log(math.add(5, 3));  // Output: 8
console.log(math.subtract(5, 3));  // Output: 2
```

## 7. Asynchronous Programming

Node.js uses non-blocking, event-driven architecture. Promises and async/await make handling asynchronous code easier.

Example using Promises:

```javascript
const fs = require('fs').promises;

fs.readFile('example.txt', 'utf8')
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

Example using async/await:

```javascript
const fs = require('fs').promises;

async function readFile() {
  try {
    const data = await fs.readFile('example.txt', 'utf8');
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}

readFile();
```

## 8. Using npm Packages

npm is the default package manager for Node.js. You can install and use third-party packages from the npm registry.

Example of installing and using a package (`axios` for making HTTP requests):

Install axios:

```bash
npm install axios
```

Use axios in your project:

```javascript
const axios = require('axios');

axios.get('https://api.github.com/users/github')
  .then(response => console.log(response.data))
  .catch(error => console.error(error));
```

## 9. Handling HTTP Requests with Express.js

Express.js is a popular framework for building web applications in Node.js.

Install Express.js:

```bash
npm install express
```

Create a basic Express server:

```javascript
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

## 10. Connecting to a Database

Node.js can connect to various databases. Here’s an example using MongoDB with Mongoose:

Install Mongoose:

```bash
npm install mongoose
```

Connect to MongoDB and define a model:

```javascript
const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost:27017/myapp', { useNewUrlParser: true, useUnifiedTopology: true });

const User = mongoose.model('User', { name: String });

const user = new User({ name: 'John Doe' });
user.save().then(() => console.log('User added'));
```

## 11. Environment Variables

Environment variables are used for configuration.

Install dotenv:

```bash
npm install dotenv
```

Create a `.env` file:

```
PORT=3000
DB_HOST=localhost
DB_USER=root
DB_PASS=s1mpl3
```

Use environment variables in your project:

```javascript
require('dotenv').config();

const port = process.env.PORT;

app.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});
```

## 12. Logging

For logging, you can use the winston package.

Install winston:

```bash
npm install winston
```

Configure and use winston:

```javascript
const winston = require('winston');

const logger = winston.createLogger({
  level: 'info',
  format: winston.format.json(),
  transports: [
    new winston.transports.File({ filename: 'error.log', level: 'error' }),
    new winston.transports.File({ filename: 'combined.log' }),
  ],
});

logger.info('Hello, winston!');
```

## 13. Testing

For testing, you can use frameworks like Mocha, Chai, and Supertest.

Install testing libraries:

```bash
npm install mocha chai supertest
```

Write tests:

```javascript
// test/test.js
const chai = require('chai');
const chaiHttp = require('chai-http');
const server = require('../index');
const should = chai.should();

chai.use(chaiHttp);

describe('GET /', () => {
  it('should return Hello, Express!', (done) => {
    chai.request(server)
      .get('/')
      .end((err, res) => {
        res.should.have.status(200);
        res.text.should.equal('Hello, Express!');
        done();
      });
  });
});
```

Run tests:

```bash
npx mocha
```

## 14. Error Handling

Proper error handling is crucial in Node.js applications.

Example of a middleware for error handling:

```javascript
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```

## 15. File Uploads

To handle file uploads, you can use the multer package.

Install multer:

```bash
npm install multer
```

Use multer to handle file uploads:

```javascript
const multer = require('multer');
const upload = multer({ dest: 'uploads/' });

app.post('/upload', upload.single('file'), (req, res) => {
  res.send(`File uploaded: ${req.file.filename}`);
});
```

## 16. WebSockets

For real-time communication, you can use WebSockets. Here’s an example using socket.io:

Install socket.io:

```bash
npm install socket.io
```

Set up a WebSocket server:

```javascript
const http = require('http');
const socketIo = require('socket.io');

const server = http.createServer(app);
const io = socketIo(server);

io.on('connection', (socket) => {
  console.log('a user connected');
  socket.on('disconnect', () => {
    console.log('user disconnected');
  });
});

server.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});
```

## 17. Deployment

To deploy your Node.js application, you can use services like Heroku, Vercel, or your own server.

Example deployment to Heroku:

Install the Heroku CLI and log in:

```bash
npm install -g heroku
heroku login
```

Create a Procfile in the root of your project:

```
web: node index.js
```

Initialize a git repository, commit your code, and push to Heroku:

```bash
git init
heroku create
git add .
git commit -m "Initial commit"
git push heroku master
```

Open your application:

```bash
heroku open
```

## 18. Best Practices

- Follow coding standards and best practices.
- Use environment variables for configuration.
- Write tests and maintain test coverage.
- Handle errors gracefully.
- Secure your application (sanitize inputs, validate data).
- Monitor performance and debug performance issues.
- Use logging effectively for debugging and monitoring.

## 19. Useful Resources

- [Node.js Official Documentation](https://nodejs.org)
- [npm Documentation](https://docs.npmjs.com)
- [Express.js Official Documentation](https://expressjs.com)
- [Mozilla Developer