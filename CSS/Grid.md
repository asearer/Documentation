### Guide to CSS Grid

CSS Grid Layout, commonly referred to as Grid, is a powerful layout system available in CSS. It allows you to create complex web designs with ease by providing a grid-based layout system, with rows and columns, making it a two-dimensional layout system unlike Flexbox which is primarily one-dimensional.

#### 1. Basics of CSS Grid

CSS Grid introduces a grid container and grid items.

- **Grid Container**: An element with `display: grid` or `display: inline-grid`.
- **Grid Items**: The direct children of a grid container.

#### 2. Grid Container Properties

These properties are applied to the grid container to define the layout of the grid items.

- **display**
  ```css
  .container {
    display: grid; /* or inline-grid */
  }
  ```

- **grid-template-columns**
  Defines the columns of the grid.
  ```css
  .container {
    grid-template-columns: 100px 100px 100px; /* 3 columns, each 100px wide */
    grid-template-columns: 1fr 2fr; /* 2 columns, first takes 1 fraction unit, second takes 2 fraction units */
    grid-template-columns: repeat(3, 1fr); /* 3 columns, each 1 fraction unit wide */
  }
  ```

- **grid-template-rows**
  Defines the rows of the grid.
  ```css
  .container {
    grid-template-rows: 100px 200px; /* 2 rows, first 100px high, second 200px high */
    grid-template-rows: repeat(2, 1fr); /* 2 rows, each taking 1 fraction unit */
  }
  ```

- **grid-template-areas**
  Defines grid areas.
  ```css
  .container {
    grid-template-areas: 
      "header header header"
      "main main sidebar"
      "footer footer footer";
  }
  .header {
    grid-area: header;
  }
  .main {
    grid-area: main;
  }
  .sidebar {
    grid-area: sidebar;
  }
  .footer {
    grid-area: footer;
  }
  ```

- **gap** (or `grid-gap`)
  Defines the gaps between rows and columns.
  ```css
  .container {
    gap: 10px; /* 10px gap between both rows and columns */
    row-gap: 10px; /* 10px gap between rows */
    column-gap: 20px; /* 20px gap between columns */
  }
  ```

- **grid-auto-rows** and **grid-auto-columns**
  Defines the size of implicitly created rows or columns.
  ```css
  .container {
    grid-auto-rows: 100px;
    grid-auto-columns: 100px;
  }
  ```

- **grid-auto-flow**
  Controls how auto-placed items are inserted in the grid.
  ```css
  .container {
    grid-auto-flow: row; /* default */
    grid-auto-flow: column;
    grid-auto-flow: dense; /* fills holes in the grid */
  }
  ```

#### 3. Grid Item Properties

These properties are applied to the grid items within the grid container.

- **grid-column-start** and **grid-column-end**
  Defines the start and end position of a grid item.
  ```css
  .item {
    grid-column-start: 1;
    grid-column-end: 3; /* spans 2 columns */
  }
  ```

- **grid-row-start** and **grid-row-end**
  Defines the start and end position of a grid item.
  ```css
  .item {
    grid-row-start: 1;
    grid-row-end: 3; /* spans 2 rows */
  }
  ```

- **grid-column** and **grid-row**
  Shorthand for the start and end properties.
  ```css
  .item {
    grid-column: 1 / 3; /* spans 2 columns */
    grid-row: 1 / 3; /* spans 2 rows */
  }
  ```

- **grid-area**
  Shorthand for specifying the grid item's row start, column start, row end, and column end in one line.
  ```css
  .item {
    grid-area: 1 / 1 / 3 / 3; /* row-start / column-start / row-end / column-end */
  }
  ```

- **justify-self**
  Aligns the item within its column.
  ```css
  .item {
    justify-self: start; /* default is stretch */
    justify-self: end;
    justify-self: center;
  }
  ```

- **align-self**
  Aligns the item within its row.
  ```css
  .item {
    align-self: start; /* default is stretch */
    align-self: end;
    align-self: center;
  }
  ```

- **place-self**
  Shorthand for `align-self` and `justify-self`.
  ```css
  .item {
    place-self: center start; /* align-self / justify-self */
  }
  ```

#### 4. Example Layouts with CSS Grid

Here are a few examples of common layouts you can achieve with CSS Grid:

- **Simple Grid Layout**
  ```css
  .container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
  }
  .item {
    background: lightgrey;
    padding: 20px;
  }
  ```

- **Nested Grid Layout**
  ```css
  .container {
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 10px;
  }
  .nested-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 5px;
  }
  ```

- **Responsive Grid Layout**
  ```css
  .container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
    gap: 10px;
  }
  ```

- **Grid Layout with Named Areas**
  ```css
  .container {
    display: grid;
    grid-template-areas: 
      "header header"
      "main sidebar"
      "footer footer";
    grid-template-columns: 2fr 1fr;
    gap: 10px;
  }
  .header {
    grid-area: header;
  }
  .main {
    grid-area: main;
  }
  .sidebar {
    grid-area: sidebar;
  }
  .footer {
    grid-area: footer;
  }
  ```

