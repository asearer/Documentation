### Guide to Flexbox

Flexbox, short for "Flexible Box Layout," is a CSS layout model that allows you to design complex and efficient layouts with ease. Here’s a detailed guide to understanding and using Flexbox.

#### 1. Basics of Flexbox

Flexbox is designed for one-dimensional layouts, meaning you can control the layout in one direction at a time (either as a row or a column). The key components of a Flexbox layout are the **flex container** and **flex items**.

- **Flex Container**: An element that has `display: flex` or `display: inline-flex`.
- **Flex Items**: The direct children of a flex container.

#### 2. Flex Container Properties

These properties are applied to the flex container to define the layout of the flex items.

- **display**
  ```css
  .container {
    display: flex; /* or inline-flex */
  }
  ```

- **flex-direction**
  Defines the direction of the main axis.
  ```css
  .container {
    flex-direction: row; /* default */
    flex-direction: row-reverse;
    flex-direction: column;
    flex-direction: column-reverse;
  }
  ```

- **flex-wrap**
  Controls whether the flex container is a single-line or multi-line flex container.
  ```css
  .container {
    flex-wrap: nowrap; /* default */
    flex-wrap: wrap;
    flex-wrap: wrap-reverse;
  }
  ```

- **flex-flow**
  A shorthand for `flex-direction` and `flex-wrap`.
  ```css
  .container {
    flex-flow: row wrap;
  }
  ```

- **justify-content**
  Defines how flex items are aligned along the main axis.
  ```css
  .container {
    justify-content: flex-start; /* default */
    justify-content: flex-end;
    justify-content: center;
    justify-content: space-between;
    justify-content: space-around;
    justify-content: space-evenly;
  }
  ```

- **align-items**
  Defines how flex items are aligned along the cross axis.
  ```css
  .container {
    align-items: stretch; /* default */
    align-items: flex-start;
    align-items: flex-end;
    align-items: center;
    align-items: baseline;
  }
  ```

- **align-content**
  Aligns the flex lines when there is extra space in the cross axis.
  ```css
  .container {
    align-content: stretch; /* default */
    align-content: flex-start;
    align-content: flex-end;
    align-content: center;
    align-content: space-between;
    align-content: space-around;
  }
  ```

#### 3. Flex Item Properties

These properties are applied to the flex items within the flex container.

- **order**
  Controls the order of the flex items.
  ```css
  .item {
    order: 0; /* default */
  }
  ```

- **flex-grow**
  Defines the ability of a flex item to grow if necessary.
  ```css
  .item {
    flex-grow: 0; /* default */
    flex-grow: 1; /* The item will grow to fill available space */
  }
  ```

- **flex-shrink**
  Defines the ability of a flex item to shrink if necessary.
  ```css
  .item {
    flex-shrink: 1; /* default */
    flex-shrink: 0; /* The item will not shrink */
  }
  ```

- **flex-basis**
  Defines the default size of an element before the remaining space is distributed.
  ```css
  .item {
    flex-basis: auto; /* default */
    flex-basis: 50%; /* 50% of the container */
    flex-basis: 100px; /* 100px width */
  }
  ```

- **flex**
  A shorthand for `flex-grow`, `flex-shrink`, and `flex-basis`.
  ```css
  .item {
    flex: 0 1 auto; /* default */
    flex: 1; /* flex-grow: 1; flex-shrink: 1; flex-basis: 0%; */
  }
  ```

- **align-self**
  Allows the default alignment (or the one specified by `align-items`) to be overridden for individual flex items.
  ```css
  .item {
    align-self: auto; /* default */
    align-self: flex-start;
    align-self: flex-end;
    align-self: center;
    align-self: baseline;
    align-self: stretch;
  }
  ```

#### 4. Example Layouts with Flexbox

Here are a few examples of common layouts you can achieve with Flexbox:

- **Horizontal Centering**
  ```css
  .container {
    display: flex;
    justify-content: center;
  }
  ```

- **Vertical Centering**
  ```css
  .container {
    display: flex;
    align-items: center;
  }
  ```

- **Horizontal and Vertical Centering**
  ```css
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  ```

- **Flexible Layout with Different Sized Items**
  ```css
  .container {
    display: flex;
  }
  .item {
    flex: 1;
  }
  .item.large {
    flex: 2;
  }
  ```

- **Wrapping Flex Items**
  ```css
  .container {
    display: flex;
    flex-wrap: wrap;
  }
  .item {
    flex: 1 1 100px; /* flex-grow: 1; flex-shrink: 1; flex-basis: 100px; */
  }
  ```

