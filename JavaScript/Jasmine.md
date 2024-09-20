### Guide to Jasmine

**Jasmine** is a behavior-driven development (BDD) framework for testing JavaScript code. It does not require a DOM and is suited for testing any JavaScript application or framework. Jasmine focuses on readability and ease of use, providing a clean syntax for writing tests and assertions.

### Features of Jasmine

1. **BDD Syntax**: Descriptive syntax for defining tests and expectations.
2. **No Dependencies**: Jasmine does not require any external libraries or frameworks.
3. **Built-in Matchers**: Provides a rich set of built-in matchers for assertions.
4. **Spies**: Mock functions and track calls, arguments, and return values.
5. **Async Testing**: Supports testing asynchronous code with callbacks, Promises, or async/await.
6. **Test Doubles**: Supports mocks, stubs, and spies for flexible test setups.
7. **Browser Support**: Can run tests in the browser using the standalone version of Jasmine.

### Installation

To use Jasmine for testing Node.js applications, install it via npm:

```bash
npm install --save-dev jasmine
```

For browser-based testing, download Jasmine standalone from the [official website](https://jasmine.github.io/pages/getting_started.html).

### Writing Tests with Jasmine

#### 1. Basic Test Example

Create a file named `math.js`:

```javascript
const math = {
  add: function(a, b) {
    return a + b;
  },
  subtract: function(a, b) {
    return a - b;
  }
};

module.exports = math;
```

Create a test file named `math.spec.js`:

```javascript
const math = require('./math');

describe('Math operations', () => {
  it('should add numbers correctly', () => {
    expect(math.add(1, 2)).toBe(3);
  });

  it('should subtract numbers correctly', () => {
    expect(math.subtract(4, 2)).toBe(2);
  });
});
```

#### 2. Running Tests

For Node.js, run Jasmine from the command line:

```bash
npx jasmine
```

By default, Jasmine looks for test files with the `.spec.js` extension in the current directory and subdirectories.

### Matchers

Jasmine provides a wide range of built-in matchers for assertions:

- `expect(value).toBe(expected)`: Strict equality (`===`).
- `expect(value).toEqual(expected)`: Deep equality for objects and arrays.
- `expect(value).toBeTruthy()` / `toBeFalsy()`: Check if a value is truthy or falsy.
- `expect(value).toContain(item)`: Check if a string, array, or iterable contains an item.
- `expect(value).toThrow(error)`: Verify if a function throws an error.

### Asynchronous Testing

Jasmine supports testing asynchronous code using callbacks, Promises, or async/await:

#### Example with Callbacks

```javascript
describe('Async operations', () => {
  it('should handle async operation with callback', (done) => {
    setTimeout(() => {
      expect(1 + 1).toBe(2);
      done();
    }, 1000);
  });
});
```

#### Example with Promises

```javascript
describe('Async operations', () => {
  it('should handle async operation with Promise', () => {
    return new Promise((resolve) => {
      setTimeout(() => {
        expect(1 + 1).toBe(2);
        resolve();
      }, 1000);
    });
  });
});
```

#### Example with async/await

```javascript
describe('Async operations', () => {
  it('should handle async operation with async/await', async () => {
    await new Promise((resolve) => setTimeout(resolve, 1000));
    expect(1 + 1).toBe(2);
  });
});
```

### Spies

Jasmine allows spying on functions to track calls and arguments:

```javascript
describe('Spies', () => {
  it('should spy on a function', () => {
    const spyFunction = jasmine.createSpy('spyFunction');
    spyFunction(1, 'hello');
    expect(spyFunction).toHaveBeenCalled();
    expect(spyFunction).toHaveBeenCalledWith(1, 'hello');
  });
});
```

### Hooks

Jasmine supports `beforeAll`, `afterAll`, `beforeEach`, and `afterEach` hooks for setup and teardown:

```javascript
describe('Hooks', () => {
  beforeAll(() => {
    // runs once before all tests
  });

  afterAll(() => {
    // runs once after all tests
  });

  beforeEach(() => {
    // runs before each test
  });

  afterEach(() => {
    // runs after each test
  });

  // test cases
});
```

### Pending Tests

Mark tests as pending using `xit`, `fit`, or `pending()`:

```javascript
describe('Pending and Skipped Tests', () => {
  xit('should be skipped', () => {
    // this test will be skipped
  });

  it('should be pending');
});
```

### Custom Matchers

Define custom matchers for reusable assertions:

```javascript
beforeEach(() => {
  jasmine.addMatchers({
    toBeDivisibleBy: function(util, customEqualityTesters) {
      return {
        compare: function(actual, expected) {
          const pass = actual % expected === 0;
          return {
            pass: pass,
            message: `${actual} is ${pass ? '' : 'not '}divisible by ${expected}`
          };
        }
      };
    }
  });
});

describe('Custom Matchers', () => {
  it('should check if a number is divisible by another', () => {
    expect(10).toBeDivisibleBy(2);
  });
});
```

### Browser Testing with Jasmine

Include Jasmine standalone files (`jasmine.js` and `jasmine.css`) in your HTML to run tests in the browser:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Jasmine Tests</title>
  <link rel="stylesheet" href="path/to/jasmine.css">
  <script src="path/to/jasmine.js"></script>
  <script src="path/to/jasmine-html.js"></script>
  <script src="path/to/boot.js"></script>
</head>
<body>
  <!-- Your tests here -->
</body>
</html>
```

### Configuration

Jasmine can be configured using `jasmine.json` or by passing options directly to `jasmine.init`.

#### Example `jasmine.json`:

```json
{
  "spec_dir": "spec",
  "spec_files": ["**/*[sS]pec.js"],
  "helpers": ["helpers/**/*.js"],
  "stopSpecOnExpectationFailure": false,
  "random": true
}
```

### Conclusion

Jasmine is a powerful BDD testing framework for JavaScript applications, offering a clean syntax, rich set of features, and flexibility for testing Node.js and browser-based applications. By following this comprehensive guide and exploring Jasmine's capabilities, you can effectively test your JavaScript codebase, ensuring reliability and maintaining quality throughout development.