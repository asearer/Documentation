**Express.js methods**, middleware, and utilities that are commonly used for building web applications and APIs:

---

### **1. Application-Level Methods**

These methods are available on the Express **app** object, which is the main application object.

- **`app.listen(port, [hostname], [backlog], [callback])`**:  
  Starts a server that listens for incoming connections on the given port.

  ```js
  const express = require('express');
  const app = express();

  app.listen(3000, () => {
    console.log('Server is running on port 3000');
  });
  ```

- **`app.get(path, callback)`**:  
  Defines a route that listens for GET requests at the given path.

  ```js
  app.get('/', (req, res) => {
    res.send('Hello, World!');
  });
  ```

- **`app.post(path, callback)`**:  
  Defines a route that listens for POST requests.

  ```js
  app.post('/submit', (req, res) => {
    res.send('Form submitted');
  });
  ```

- **`app.put(path, callback)`**:  
  Defines a route that listens for PUT requests (for updating resources).

- **`app.delete(path, callback)`**:  
  Defines a route that listens for DELETE requests (for deleting resources).

- **`app.use([path], middleware)`**:  
  Mounts middleware to handle requests at a specific path or globally for the entire app.  
  Without a path, it applies the middleware to all routes.

  ```js
  app.use(express.json()); // Apply middleware to parse JSON requests
  ```

- **`app.set(name, value)`**:  
  Sets app-level variables such as settings or configuration options.

  ```js
  app.set('view engine', 'pug'); // Set Pug as the view engine
  ```

- **`app.get(name)`**:  
  Gets the value of app-level variables (retrieves app settings).

  ```js
  const viewEngine = app.get('view engine');
  console.log(viewEngine); // Output: pug
  ```

- **`app.engine(ext, callback)`**:  
  Registers a template engine to render files with a specific extension.

- **`app.route(path)`**:  
  Allows you to create a chainable route handler for specific paths.

  ```js
  app.route('/book')
    .get((req, res) => res.send('Get a book'))
    .post((req, res) => res.send('Add a book'))
    .put((req, res) => res.send('Update the book'));
  ```

- **`app.locals`**:  
  Stores local variables that are shared across the app.

  ```js
  app.locals.title = 'My App'; // Accessible across all views
  ```

---

### **2. Router-Level Methods**

The `Router` object is used to create modular route handlers. These methods are similar to the app-level methods but are scoped to the `Router`.

- **`router.get(path, callback)`**:  
  Defines a GET route for the router.

  ```js
  const router = express.Router();
  router.get('/', (req, res) => {
    res.send('Router GET');
  });
  ```

- **`router.post(path, callback)`**:  
  Defines a POST route for the router.

- **`router.put(path, callback)`**:  
  Defines a PUT route for the router.

- **`router.delete(path, callback)`**:  
  Defines a DELETE route for the router.

- **`router.use([path], middleware)`**:  
  Attaches middleware functions to the router.

  ```js
  router.use((req, res, next) => {
    console.log('Middleware for this router');
    next();
  });
  ```

---

### **3. Request Object Methods (`req`)**

The `req` object represents the HTTP request and has properties and methods that help retrieve data about the request.

- **`req.query`**:  
  Contains query string parameters in the URL.

  ```js
  app.get('/search', (req, res) => {
    console.log(req.query.q); // Access ?q=searchQuery in the URL
  });
  ```

- **`req.params`**:  
  Contains route parameters defined in the URL path.

  ```js
  app.get('/user/:id', (req, res) => {
    console.log(req.params.id); // Access :id from /user/:id
  });
  ```

- **`req.body`**:  
  Contains data sent in the body of POST/PUT requests (parsed with middleware).

  ```js
  app.use(express.json()); // Middleware to parse JSON body
  app.post('/submit', (req, res) => {
    console.log(req.body); // Access the parsed request body
  });
  ```

- **`req.headers`**:  
  Contains the headers sent with the request.

  ```js
  console.log(req.headers['content-type']);
  ```

- **`req.cookies`**:  
  Contains the cookies sent with the request (requires cookie-parsing middleware).

  ```js
  const cookieParser = require('cookie-parser');
  app.use(cookieParser());

  app.get('/', (req, res) => {
    console.log(req.cookies); // Access cookies
  });
  ```

- **`req.ip`**:  
  Returns the remote IP address of the request.

- **`req.method`**:  
  Returns the HTTP method (GET, POST, etc.).

- **`req.path`**:  
  Returns the request path (URL without query string).

- **`req.originalUrl`**:  
  Returns the full original URL.

- **`req.get(headerName)`**:  
  Retrieves the value of a specific request header.

  ```js
  console.log(req.get('User-Agent'));
  ```

---

### **4. Response Object Methods (`res`)**

The `res` object represents the HTTP response and has methods for sending data back to the client.

- **`res.send(body)`**:  
  Sends the HTTP response. The `body` can be a string, buffer, or object.

  ```js
  res.send('Hello, World!'); // Sends plain text response
  res.send({ message: 'Hello' }); // Sends JSON response
  ```

- **`res.json(body)`**:  
  Sends a JSON response, automatically converting the body to JSON.

  ```js
  res.json({ message: 'Hello, World!' });
  ```

- **`res.status(statusCode)`**:  
  Sets the HTTP status code for the response.

  ```js
  res.status(404).send('Not Found');
  ```

- **`res.sendFile(path)`**:  
  Sends a file as the response.

  ```js
  const path = require('path');
  res.sendFile(path.join(__dirname, 'index.html'));
  ```

- **`res.redirect(statusCode, url)`**:  
  Redirects the client to another URL.

  ```js
  res.redirect(301, '/new-location'); // Redirect with 301 status code
  ```

- **`res.set(field, value)`**:  
  Sets the value of an HTTP response header.

  ```js
  res.set('Content-Type', 'application/json');
  ```

- **`res.cookie(name, value, [options])`**:  
  Sets a cookie to be sent in the response (requires cookie-parser).

  ```js
  res.cookie('name', 'value', { maxAge: 900000, httpOnly: true });
  ```

- **`res.clearCookie(name, [options])`**:  
  Clears a cookie from the response.

- **`res.render(view, [locals], callback)`**:  
  Renders a view template with the provided locals (data).

  ```js
  res.render('index', { title: 'Express App' });
  ```

---

### **5. Middleware**

Middleware functions are functions that have access to the request (`req`), response (`res`), and next (`next`) objects. They are used to modify or handle requests before reaching routes or after the response is sent.

- **`express.json()`**:  
  Built-in middleware to parse incoming JSON requests.

  ```js
  app.use(express.json());
  ```

- **`express.urlencoded(options)`**:  
  Middleware to parse URL-encoded request bodies.

  ```js
  app.use(express.urlencoded({ extended: true }));
  ```

- **`next()`**:  
  Invokes the next middleware function in the stack. If no middleware is left, it sends the response.

  ```js
  app.use((req, res, next) => {
    console.log('Middleware function');
    next();
  });
  ```

- **Error-handling middleware**:  
  Middleware that handles errors (must have 4 arguments).

  ```js
  app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).send('Something broke!');
  });
  ```

---

### **6. Template Engines**

Express supports rendering dynamic HTML using template engines.

- **`app.set('view engine', 'engine')`**:  
  Sets the template engine for rendering views.

  ```js
  app.set('view engine', 'pug');
  ```

- **`app.set('views', path)`**:  
  Sets the directory where view templates are located.

  ```js
  const

 path = require('path');
  app.set('views', path.join(__dirname, 'views'));
  ```

---