### Guide to CSS

**CSS (Cascading Style Sheets)** is a stylesheet language used to describe the presentation of a document written in HTML or XML. CSS describes how elements should be rendered on screen, on paper, in speech, or on other media.

### Basic Structure of a CSS Rule

A CSS rule consists of a selector and a declaration block. The selector points to the HTML element you want to style. The declaration block contains one or more declarations separated by semicolons.

```css
selector {
    property: value;
    property: value;
}
```

### CSS Selectors

CSS selectors are used to "find" (or select) the HTML elements you want to style.

#### Basic Selectors

- **Element Selector**: Selects all elements of a given type.

  ```css
  p {
      color: blue;
  }
  ```

- **ID Selector**: Selects a single element with a specific ID. The ID is unique within a page.

  ```css
  #unique-element {
      background-color: yellow;
  }
  ```

- **Class Selector**: Selects all elements with a specific class.

  ```css
  .class-name {
      font-size: 16px;
  }
  ```

- **Universal Selector**: Selects all elements.

  ```css
  * {
      margin: 0;
      padding: 0;
  }
  ```

#### Combinators

- **Descendant Selector**: Selects all elements that are descendants of a specified element.

  ```css
  div p {
      color: red;
  }
  ```

- **Child Selector**: Selects all elements that are direct children of a specified element.

  ```css
  div > p {
      font-weight: bold;
  }
  ```

- **Adjacent Sibling Selector**: Selects an element that is the next sibling of a specified element.

  ```css
  h1 + p {
      margin-top: 0;
  }
  ```

- **General Sibling Selector**: Selects all elements that are siblings of a specified element.

  ```css
  h1 ~ p {
      color: green;
  }
  ```

### CSS Properties

CSS properties are used to apply styles to HTML elements. Here are some of the most common properties:

#### Text Properties

- **color**: Sets the color of the text.

  ```css
  p {
      color: blue;
  }
  ```

- **font-size**: Sets the size of the text.

  ```css
  p {
      font-size: 14px;
  }
  ```

- **font-family**: Specifies the font for an element.

  ```css
  p {
      font-family: Arial, sans-serif;
  }
  ```

- **font-weight**: Sets the weight (boldness) of the text.

  ```css
  p {
      font-weight: bold;
  }
  ```

- **text-align**: Sets the horizontal alignment of the text.

  ```css
  p {
      text-align: center;
  }
  ```

#### Background Properties

- **background-color**: Sets the background color of an element.

  ```css
  div {
      background-color: lightblue;
  }
  ```

- **background-image**: Sets a background image for an element.

  ```css
  div {
      background-image: url('image.jpg');
  }
  ```

- **background-size**: Specifies the size of the background image.

  ```css
  div {
      background-size: cover;
  }
  ```

#### Box Model Properties

- **width**: Sets the width of an element.

  ```css
  div {
      width: 100px;
  }
  ```

- **height**: Sets the height of an element.

  ```css
  div {
      height: 200px;
  }
  ```

- **padding**: Sets the padding inside an element.

  ```css
  div {
      padding: 10px;
  }
  ```

- **margin**: Sets the margin outside an element.

  ```css
  div {
      margin: 20px;
  }
  ```

- **border**: Sets the border around an element.

  ```css
  div {
      border: 1px solid black;
  }
  ```

#### Display Properties

- **display**: Specifies the display behavior of an element.

  ```css
  .hidden {
      display: none;
  }
  ```

- **visibility**: Specifies whether an element is visible or hidden.

  ```css
  .invisible {
      visibility: hidden;
  }
  ```

#### Positioning Properties

- **position**: Specifies the positioning method used for an element (static, relative, absolute, fixed, sticky).

  ```css
  .relative {
      position: relative;
      top: 10px;
      left: 20px;
  }
  ```

- **z-index**: Specifies the stack order of an element.

  ```css
  .top {
      z-index: 10;
  }
  ```

- **top, right, bottom, left**: Specifies the offsets for positioned elements.

  ```css
  .absolute {
      position: absolute;
      top: 50px;
      left: 100px;
  }
  ```

### Advanced CSS Techniques

#### Flexbox

Flexbox is a layout module that provides an easy and clean way to arrange items within a container.

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

#### Grid

CSS Grid Layout is a 2-dimensional system for laying out items on a webpage.

```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 10px;
}
```

#### Media Queries

Media queries are used to apply different styles for different devices or screen sizes.

```css
@media (max-width: 600px) {
    .responsive {
        font-size: 12px;
    }
}
```

#### Pseudo-classes and Pseudo-elements

Pseudo-classes and pseudo-elements allow you to style elements based on their state or position.

- **:hover**: Applies when the user hovers over an element.

  ```css
  a:hover {
      color: red;
  }
  ```

- **:first-child**: Applies to the first child of an element.

  ```css
  p:first-child {
      font-weight: bold;
  }
  ```

- **::before**: Inserts content before an element.

  ```css
  p::before {
      content: "Note: ";
      font-weight: bold;
  }
  ```

- **::after**: Inserts content after an element.

  ```css
  p::after {
      content: " - end";
  }
  ```

### CSS Variables

CSS variables (custom properties) allow you to store values that you want to reuse throughout a document.

```css
:root {
    --main-color: #3498db;
    --secondary-color: #2ecc71;
}

body {
    color: var(--main-color);
}

h1 {
    background-color: var(--secondary-color);
}
```

### CSS Frameworks and Preprocessors

#### CSS Frameworks

CSS frameworks like Bootstrap, Foundation, and Tailwind CSS provide pre-written CSS rules and components to help you build responsive and modern websites quickly.

#### CSS Preprocessors

CSS preprocessors like Sass, Less, and Stylus extend CSS with variables, nested rules, and functions, making CSS more maintainable and easier to write.

```scss
$primary-color: #333;

body {
    color: $primary-color;
    
    nav {
        background: lighten($primary-color, 20%);
    }
}
```

### Best Practices for CSS

1. **Organize Your CSS**: Keep your CSS organized by grouping related styles and using comments.
2. **Use Classes Instead of IDs**: Prefer classes for styling to avoid specificity issues.
3. **Minimize Use of !important**: Avoid using `!important` unless absolutely necessary, as it makes debugging harder.
4. **Write Reusable Code**: Write CSS that can be reused across multiple elements and pages.
5. **Use a CSS Reset**: Use a CSS reset to ensure consistency across different browsers.
6. **Optimize for Performance**: Minimize the number of CSS rules and avoid deeply nested selectors for better performance.

