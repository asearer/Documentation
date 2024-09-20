**Node.js methods** and **APIs** that are commonly used for server-side development:

### **1. Core Modules**

Node.js provides several **core modules** to handle various functionalities. These modules do not require installation and can be used by simply importing them using `require`.

#### **File System (fs)**

The `fs` module allows interaction with the file system.

- **`fs.readFile(path, callback)`**:  
  Reads a file asynchronously.

  ```js
  const fs = require('fs');
  fs.readFile('file.txt', 'utf8', (err, data) => {
    if (err) throw err;
    console.log(data);
  });
  ```

- **`fs.writeFile(path, data, callback)`**:  
  Writes data to a file asynchronously, creating the file if it does not exist.

  ```js
  fs.writeFile('file.txt', 'Hello, World!', (err) => {
    if (err) throw err;
    console.log('File written');
  });
  ```

- **`fs.appendFile(path, data, callback)`**:  
  Appends data to a file.

  ```js
  fs.appendFile('file.txt', 'Additional content', (err) => {
    if (err) throw err;
    console.log('Content appended');
  });
  ```

- **`fs.unlink(path, callback)`**:  
  Deletes a file.

  ```js
  fs.unlink('file.txt', (err) => {
    if (err) throw err;
    console.log('File deleted');
  });
  ```

- **`fs.rename(oldPath, newPath, callback)`**:  
  Renames or moves a file.

  ```js
  fs.rename('old.txt', 'new.txt', (err) => {
    if (err) throw err;
    console.log('File renamed');
  });
  ```

#### **HTTP Module**

The `http` module is used to create an HTTP server and handle client requests and responses.

- **`http.createServer(callback)`**:  
  Creates an HTTP server that listens for requests.

  ```js
  const http = require('http');

  const server = http.createServer((req, res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type', 'text/plain');
    res.end('Hello, World!\n');
  });

  server.listen(3000, '127.0.0.1', () => {
    console.log('Server running at http://127.0.0.1:3000/');
  });
  ```

- **`req.method`**:  
  Retrieves the HTTP request method (GET, POST, etc.).

- **`req.url`**:  
  Retrieves the URL from the request object.

- **`res.writeHead(statusCode, headers)`**:  
  Sets the HTTP status code and headers for the response.

- **`res.end([data])`**:  
  Ends the response process, optionally sending data.

#### **URL Module**

The `url` module provides utilities for URL resolution and parsing.

- **`url.parse(urlString, parseQueryString)`**:  
  Parses a URL string and returns an object with URL components.

  ```js
  const url = require('url');
  const parsedUrl = url.parse('https://example.com/path?name=John', true);
  console.log(parsedUrl.query.name); // Output: John
  ```

- **`url.format(urlObject)`**:  
  Returns a formatted URL string from a URL object.

  ```js
  const formattedUrl = url.format({
    protocol: 'https',
    hostname: 'example.com',
    pathname: '/path',
    query: { name: 'John' },
  });
  console.log(formattedUrl); // Output: https://example.com/path?name=John
  ```

#### **Path Module**

The `path` module provides utilities for working with file and directory paths.

- **`path.join([...paths])`**:  
  Joins all given path segments into one path.

  ```js
  const path = require('path');
  const filePath = path.join(__dirname, 'files', 'example.txt');
  console.log(filePath);
  ```

- **`path.resolve([...paths])`**:  
  Resolves a sequence of paths into an absolute path.

  ```js
  const absolutePath = path.resolve('file.txt');
  console.log(absolutePath);
  ```

- **`path.basename(path)`**:  
  Returns the last portion of a path (the filename).

  ```js
  const filename = path.basename('/path/to/file.txt');
  console.log(filename); // Output: file.txt
  ```

- **`path.extname(path)`**:  
  Returns the extension of the path.

  ```js
  const ext = path.extname('index.html');
  console.log(ext); // Output: .html
  ```

#### **Events Module**

The `events` module allows you to work with events and event-driven programming.

- **`EventEmitter.on(eventName, listener)`**:  
  Registers an event listener for a specific event.

  ```js
  const EventEmitter = require('events');
  const emitter = new EventEmitter();

  emitter.on('message', (data) => {
    console.log(`Message received: ${data}`);
  });

  emitter.emit('message', 'Hello World');
  ```

- **`EventEmitter.emit(eventName, [args])`**:  
  Emits an event, optionally passing arguments to the listeners.

- **`EventEmitter.removeListener(eventName, listener)`**:  
  Removes a specific listener for the given event.

#### **Streams Module**

The `stream` module provides APIs for working with streams of data.

- **`stream.Readable`**:  
  Readable streams allow you to read data in chunks.

  ```js
  const fs = require('fs');
  const readable = fs.createReadStream('file.txt');
  readable.on('data', (chunk) => {
    console.log(`Chunk: ${chunk}`);
  });
  ```

- **`stream.Writable`**:  
  Writable streams allow you to write data in chunks.

  ```js
  const writable = fs.createWriteStream('file.txt');
  writable.write('Hello, World!');
  writable.end();
  ```

- **`pipe()`**:  
  Pipes a readable stream into a writable stream.

  ```js
  readable.pipe(writable);
  ```

#### **Crypto Module**

The `crypto` module provides cryptographic functionalities.

- **`crypto.createHash(algorithm)`**:  
  Creates a hash object that can be used to generate hash digests.

  ```js
  const crypto = require('crypto');
  const hash = crypto.createHash('sha256');
  hash.update('password');
  console.log(hash.digest('hex'));
  ```

- **`crypto.createCipheriv(algorithm, key, iv)`**:  
  Creates a cipher object for encryption.

- **`crypto.createDecipheriv(algorithm, key, iv)`**:  
  Creates a decipher object for decryption.

#### **OS Module**

The `os` module provides operating system-related utilities.

- **`os.cpus()`**:  
  Returns an array of information about the computer’s CPUs.

  ```js
  const os = require('os');
  console.log(os.cpus());
  ```

- **`os.freemem()`**:  
  Returns the amount of free system memory.

- **`os.homedir()`**:  
  Returns the path of the current user's home directory.

- **`os.platform()`**:  
  Returns the operating system platform (e.g., 'linux', 'darwin', 'win32').

- **`os.uptime()`**:  
  Returns the system uptime in seconds.

---

### **2. Global Objects and Functions**

Node.js provides several global objects and functions, which are available in all modules.

- **`__dirname`**:  
  The directory name of the current module.

  ```js
  console.log(__dirname); // Outputs the current directory
  ```

- **`__filename`**:  
  The filename of the current module.

  ```js
  console.log(__filename); // Outputs the current file's absolute path
  ```

- **`require(moduleName)`**:  
  Used to import modules.

  ```js
  const fs = require('fs');
  ```

- **`module.exports`**:  
  Used to export functions or objects from a module to be used in other files.

  ```js
  module.exports = myFunction;
  ```

- **`process`**:  
  Provides information and control over the current Node.js process.

  - **`process.env`**:  
    Provides access to environment variables.
  
  - **`process.exit([code])`**:  
    Exits the current process with an optional exit code.
  
  - **`process.argv`**:  
    An array containing command-line arguments passed when launching the Node.js process.

    ```js
    process.argv.forEach((val, index) => {
      console.log(`${index}: ${val}`);
    });
    ```

  - **`process.nextTick(callback)`**:  
    Defers the execution of a function until the next event loop cycle.

---

### **3. Timers**

Node.js provides global methods to handle timeouts and intervals.

- **`setTimeout(callback, delay, [...args])`**:  
  Calls the callback function after a specified delay.

  ```js
  setTimeout(() => {
    console.log('Timeout

 after 1 second');
  }, 1000);
  ```

- **`setInterval(callback, interval, [...args])`**:  
  Calls the callback function at specified intervals.

  ```js
  setInterval(() => {
    console.log('Called every 2 seconds');
  }, 2000);
  ```

- **`clearTimeout(timeoutObject)`**:  
  Cancels a timeout that was set by `setTimeout`.

- **`clearInterval(intervalObject)`**:  
  Cancels an interval that was set by `setInterval`.

---

### **4. Child Processes**

The `child_process` module enables you to spawn new processes.

- **`child_process.exec(command, callback)`**:  
  Executes a shell command and buffers the output.

  ```js
  const { exec } = require('child_process');
  exec('ls', (error, stdout, stderr) => {
    if (error) {
      console.error(`Error: ${error.message}`);
    }
    console.log(`stdout: ${stdout}`);
  });
  ```

- **`child_process.spawn(command, args)`**:  
  Spawns a new process, returning streams for `stdout` and `stderr`.

---

### **5. Buffer**

The `Buffer` class is used to handle binary data directly in Node.js.

- **`Buffer.from(string, encoding)`**:  
  Creates a new buffer containing the given string.

  ```js
  const buffer = Buffer.from('Hello', 'utf-8');
  console.log(buffer.toString());
  ```

- **`buffer.toString([encoding])`**:  
  Decodes and returns the buffer as a string.

- **`Buffer.alloc(size)`**:  
  Allocates a new buffer of the given size.

---

### **6. Process and Cluster**

- **`process.env`**:  
  Provides access to the environment variables of the current process.

- **`cluster.fork()`**:  
  Creates a new worker process.

- **`cluster.isMaster`**:  
  Checks if the current process is the master process.

  ```js
  const cluster = require('cluster');
  if (cluster.isMaster) {
    // Master process
    cluster.fork(); // Fork a new worker process
  } else {
    // Worker process
  }
  ```

---

### **7. HTTP/2 (Node >= v8.4.0)**

The `http2` module is used to enable HTTP/2 support in Node.js.

- **`http2.createServer(callback)`**:  
  Creates an HTTP/2 server.

  ```js
  const http2 = require('http2');
  const server = http2.createServer((req, res) => {
    res.end('Hello, HTTP/2!');
  });
  ```

---

### **8. Promisified fs Module (Node >= v10)**

Starting from Node v10, you can use the **`fs.promises`** API to work with file system operations using promises.

- **`fs.promises.readFile(path)`**:  
  Asynchronously reads the contents of a file, returning a promise.

  ```js
  const fs = require('fs').promises;
  async function readFile() {
    const data = await fs.readFile('file.txt', 'utf8');
    console.log(data);
  }
  ```

- **`fs.promises.writeFile(path, data)`**:  
  Asynchronously writes data to a file, returning a promise.

---