### 1. **Custom Data Attributes**

Custom data attributes allow you to store extra information on HTML elements. These attributes start with `data-` and can be accessed via JavaScript.

#### Usage:

- **HTML:**

  ```html
  <div data-user-id="12345" data-role="admin">User Info</div>
  ```

- **JavaScript:**

  ```javascript
  const element = document.querySelector('[data-user-id]');
  const userId = element.getAttribute('data-user-id');
  const role = element.dataset.role; // Alternative way to access data attributes
  console.log(userId, role);
  ```

**Use Cases:** Store metadata or configuration settings associated with elements.

### 2. **Web Components**

Web Components allow you to create custom, reusable HTML elements with encapsulated HTML, CSS, and JavaScript. They consist of:

- **Custom Elements:** Define new HTML elements.
- **Shadow DOM:** Encapsulate styles and markup.
- **HTML Templates:** Define markup fragments for reuse.

#### Example:

- **HTML Template:**

  ```html
  <template id="my-element-template">
    <style>
      p {
        color: blue;
      }
    </style>
    <p>Hello from Web Component!</p>
  </template>
  ```

- **Custom Element Definition:**

  ```javascript
  class MyElement extends HTMLElement {
    constructor() {
      super();
      const template = document.getElementById('my-element-template').content;
      const shadowRoot = this.attachShadow({ mode: 'open' });
      shadowRoot.appendChild(template.cloneNode(true));
    }
  }

  customElements.define('my-element', MyElement);
  ```

- **Usage:**

  ```html
  <my-element></my-element>
  ```

**Use Cases:** Create reusable UI components like custom buttons or cards.

### 3. **Form Enhancements**

HTML5 introduced several new attributes and input types that enhance forms:

- **New Input Types:**

  ```html
  <input type="email" placeholder="Enter your email">
  <input type="range" min="0" max="100" value="50">
  <input type="date">
  ```

- **Form Attributes:**

  ```html
  <input type="text" required pattern="[A-Za-z]{3,}" title="Three or more letters">
  ```

- **Form Validation API:**

  ```html
  <input id="username" type="text" required>
  <script>
    document.getElementById('username').addEventListener('input', function() {
      if (this.value.length < 5) {
        this.setCustomValidity('Username must be at least 5 characters long.');
      } else {
        this.setCustomValidity('');
      }
    });
  </script>
  ```

**Use Cases:** Enhance user experience with more intuitive input elements and validation.

### 4. **ARIA (Accessible Rich Internet Applications)**

ARIA attributes improve accessibility by providing additional information to assistive technologies.

- **Common ARIA Attributes:**

  ```html
  <button aria-label="Close" onclick="closeWindow()">X</button>
  <div role="alert">This is an alert message.</div>
  ```

- **Roles:**

  ```html
  <div role="dialog" aria-labelledby="dialogTitle" aria-modal="true">
    <h2 id="dialogTitle">Dialog Title</h2>
    <p>Dialog content goes here.</p>
    <button aria-label="Close" onclick="closeDialog()">Close</button>
  </div>
  ```

**Use Cases:** Improve accessibility for users with disabilities by providing context and information to screen readers.

### 5. **HTML5 APIs**

HTML5 APIs offer advanced functionality to web applications:

- **Geolocation API:**

  ```javascript
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(function(position) {
      console.log(`Latitude: ${position.coords.latitude}, Longitude: ${position.coords.longitude}`);
    });
  }
  ```

- **Local Storage and Session Storage:**

  ```javascript
  // Local Storage
  localStorage.setItem('theme', 'dark');
  const theme = localStorage.getItem('theme');

  // Session Storage
  sessionStorage.setItem('sessionData', 'value');
  const sessionData = sessionStorage.getItem('sessionData');
  ```

- **WebSockets:**

  ```javascript
  const socket = new WebSocket('ws://example.com/socketserver');
  socket.onmessage = function(event) {
    console.log(`Message from server: ${event.data}`);
  };
  ```

**Use Cases:** Implement features like user location, persistent storage, and real-time communication.

### 6. **Canvas API**

The Canvas API allows drawing graphics directly onto the web page.

#### Example:

- **HTML:**

  ```html
  <canvas id="myCanvas" width="200" height="100"></canvas>
  ```

- **JavaScript:**

  ```javascript
  const canvas = document.getElementById('myCanvas');
  const ctx = canvas.getContext('2d');
  ctx.fillStyle = 'blue';
  ctx.fillRect(10, 10, 150, 80);
  ```

**Use Cases:** Create custom graphics, animations, and game elements.

### 7. **HTML5 Video and Audio**

HTML5 provides native support for embedding media content.

- **Video:**

  ```html
  <video width="600" controls>
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  ```

- **Audio:**

  ```html
  <audio controls>
    <source src="audio.mp3" type="audio/mp3">
    Your browser does not support the audio element.
  </audio>
  ```

**Use Cases:** Embed and control video and audio content directly within web pages.

### 8. **HTML Templates**

Templates are used to define reusable HTML fragments that are not rendered immediately but can be instantiated later.

#### Example:

- **Template Definition:**

  ```html
  <template id="myTemplate">
    <div class="template-content">Hello from the template!</div>
  </template>
  ```

- **JavaScript:**

  ```javascript
  const template = document.getElementById('myTemplate').content;
  document.body.appendChild(template.cloneNode(true));
  ```

**Use Cases:** Reuse HTML structures across your page or application.

### 9. **SVG (Scalable Vector Graphics)**

SVG allows creating vector graphics that scale without loss of quality.

#### Example:

- **Simple SVG Drawing:**

  ```html
  <svg width="100" height="100">
    <circle cx="50" cy="50" r="40" stroke="black" stroke-width="3" fill="red" />
  </svg>
  ```

**Use Cases:** Create high-quality graphics, icons, and illustrations directly in HTML.

### 10. **Embedded Content**

HTML supports embedding various types of content:

- **IFrames:**

  ```html
  <iframe src="https://example.com" width="600" height="400"></iframe>
  ```

- **Object and Embed Tags:**

  ```html
  <object data="file.pdf" type="application/pdf" width="600" height="400">
    <embed src="file.pdf" type="application/pdf" width="600" height="400">
  </object>
  ```

**Use Cases:** Embed external resources like documents, other web pages, and interactive content.

