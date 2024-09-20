**React methods**, **APIs**, and **hooks** that are commonly used in general React app development:

### **1. Component Methods (Class Components)**

These methods are available when you create **class components** in React.

- **`constructor(props)`**:  
  The constructor is called when the component is initiated. It's used to set up the initial state or bind methods.

- **`render()`**:  
  The `render` method is required in class components. It returns the JSX that defines what the UI looks like.

- **`componentDidMount()`**:  
  This method is invoked immediately after a component is mounted (inserted into the tree). Good for fetching data, setting up subscriptions, etc.

- **`componentDidUpdate(prevProps, prevState)`**:  
  Called after the component is updated, useful for performing operations when certain props or states change.

- **`componentWillUnmount()`**:  
  This is called just before a component is unmounted and destroyed. Used for cleanup (e.g., removing event listeners or timers).

- **`shouldComponentUpdate(nextProps, nextState)`**:  
  Determines if the component should update or not. Helps optimize performance by avoiding unnecessary re-renders.

- **`getSnapshotBeforeUpdate(prevProps, prevState)`**:  
  Called just before rendering new outputs, used to capture some information from the DOM (like scroll positions).

- **`componentDidCatch(error, info)`**:  
  Used to catch errors during rendering or in lifecycle methods of children components.

### **2. React Hooks (Functional Components)**

Hooks are functions that let you use state and other React features in functional components.

- **`useState(initialState)`**:  
  Manages state in functional components. Returns the current state and a function to update it.

  ```jsx
  const [state, setState] = useState(initialValue);
  ```

- **`useEffect(callback, dependencies)`**:  
  Manages side effects (e.g., data fetching, subscriptions). The callback runs after render, and the `dependencies` array controls when the effect runs.

  ```jsx
  useEffect(() => {
    // Code to run after render
    return () => {
      // Optional cleanup
    };
  }, [dependencies]);
  ```

- **`useContext(Context)`**:  
  Allows you to use the value of a context in functional components without using the `Context.Consumer` wrapper.

  ```jsx
  const contextValue = useContext(MyContext);
  ```

- **`useReducer(reducer, initialState)`**:  
  An alternative to `useState`, typically used for more complex state logic. It returns the current state and a dispatch method.

  ```jsx
  const [state, dispatch] = useReducer(reducer, initialState);
  ```

- **`useRef(initialValue)`**:  
  Returns a mutable object that persists across re-renders. Can be used to store references to DOM elements or any mutable value.

  ```jsx
  const myRef = useRef(null);
  ```

- **`useMemo(factory, dependencies)`**:  
  Memoizes a computed value to avoid re-calculating it on every render, useful for performance optimization.

  ```jsx
  const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
  ```

- **`useCallback(callback, dependencies)`**:  
  Memoizes a callback function, preventing it from being redefined unless its dependencies change.

  ```jsx
  const memoizedCallback = useCallback(() => {
    doSomething(a, b);
  }, [a, b]);
  ```

- **`useImperativeHandle(ref, createHandle, dependencies)`**:  
  Customizes the value that a parent component receives when using `ref` with a child component.

  ```jsx
  useImperativeHandle(ref, () => ({
    focus: () => {
      inputRef.current.focus();
    },
  }));
  ```

- **`useLayoutEffect(callback, dependencies)`**:  
  Similar to `useEffect`, but it fires synchronously after all DOM mutations. It can block painting.

  ```jsx
  useLayoutEffect(() => {
    // DOM changes
  }, [dependencies]);
  ```

- **`useDebugValue(value)`**:  
  Allows you to display a label for custom hooks in React DevTools.

  ```jsx
  useDebugValue(isOnline ? 'Online' : 'Offline');
  ```

### **3. JSX Methods and Attributes**

These are not "methods" in the typical sense but are syntactical features used when writing JSX in React components.

- **`className`**:  
  Used instead of `class` to apply CSS classes in JSX.

  ```jsx
  <div className="my-class"></div>
  ```

- **`style`**:  
  A prop used to apply inline styles. It accepts a JavaScript object.

  ```jsx
  <div style={{ color: 'blue', fontSize: 18 }}></div>
  ```

- **`dangerouslySetInnerHTML`**:  
  Used to inject raw HTML into a component. It's generally discouraged for security reasons.

  ```jsx
  <div dangerouslySetInnerHTML={{ __html: '<strong>Raw HTML</strong>' }}></div>
  ```

- **`key`**:  
  A unique identifier required when rendering lists of elements in React. Used to optimize rendering.

  ```jsx
  {items.map(item => (
    <div key={item.id}>{item.name}</div>
  ))}
  ```

### **4. Context API Methods**

React’s **Context API** allows for passing data through the component tree without prop drilling.

- **`React.createContext(defaultValue)`**:  
  Creates a context object that can be consumed by child components.

  ```jsx
  const MyContext = React.createContext(defaultValue);
  ```

- **`Context.Provider`**:  
  Provides the context value to child components.

  ```jsx
  <MyContext.Provider value={contextValue}>
    {children}
  </MyContext.Provider>
  ```

- **`Context.Consumer`**:  
  Consumes the context value provided by a `Provider` component.

  ```jsx
  <MyContext.Consumer>
    {value => <div>{value}</div>}
  </MyContext.Consumer>
  ```

### **5. Higher-Order Components (HOC)**

A **Higher-Order Component** is a function that takes a component and returns a new component.

- **`withRouter(Component)`**:  
  A HOC provided by `react-router` to inject routing props into a component.

  ```jsx
  export default withRouter(MyComponent);
  ```

- **`connect(mapStateToProps, mapDispatchToProps)`**:  
  A HOC provided by `react-redux` to connect a React component to a Redux store.

  ```jsx
  export default connect(mapStateToProps, mapDispatchToProps)(MyComponent);
  ```

### **6. Error Boundaries**

Error boundaries are React components that catch JavaScript errors anywhere in their child component tree.

- **`componentDidCatch(error, info)`**:  
  Lifecycle method to catch errors in class components.

  ```jsx
  class ErrorBoundary extends React.Component {
    componentDidCatch(error, info) {
      // Handle error logging
    }
    render() {
      return this.props.children;
    }
  }
  ```

### **7. React Router Methods (For Navigation)**

If you're using **React Router** for client-side routing, these are essential methods.

- **`<BrowserRouter>`**:  
  A router that uses the HTML5 history API to keep your UI in sync with the URL.

  ```jsx
  <BrowserRouter>
    <App />
  </BrowserRouter>
  ```

- **`<Route>`**:  
  Defines a route that renders a component based on the URL.

  ```jsx
  <Route path="/about" component={AboutPage} />
  ```

- **`useHistory()`**:  
  Provides access to the history instance used by React Router to programmatically navigate.

  ```jsx
  const history = useHistory();
  history.push('/new-route');
  ```

- **`useParams()`**:  
  Provides access to URL parameters.

  ```jsx
  const { id } = useParams();
  ```

- **`useLocation()`**:  
  Returns the location object that represents the current URL.

  ```jsx
  const location = useLocation();
  ```

- **`useRouteMatch()`**:  
  Provides match information for the current URL.

  ```jsx
  const match = useRouteMatch("/about");
  ```

### **8. React.memo and React.PureComponent**

React provides tools for **memoization** to optimize performance by preventing unnecessary re-renders.

- **`React.memo(Component)`**:  
  A HOC that memoizes functional components. It only re-renders the component if the props change.

  ```jsx
  const MyComponent = React.memo((props) => {
    return <div>{props.value}</div>;
  });
  ```

- **`React.PureComponent`**:  
  A base class for class components that automatically implements `shouldComponentUpdate` based on shallow comparison of props and state.

  ```jsx
  class MyComponent extends React.PureComponent {
    render() {
      return <div>{this.props.value}</div>;
    }
  }
  ```

### **9. React.Children Utility Methods**

These methods are used to manipulate and iterate over children passed to a component

.

- **`React.Children.map`**:  
  Invokes a function on every immediate child in the children prop.

  ```jsx
  React.Children.map(this.props.children, child => {
    // Do something with each child
  });
  ```

- **`React.Children.forEach`**:  
  Similar to `map` but without returning a new array.

- **`React.Children.only`**:  
  Verifies that `children` contains only one child (throws otherwise).

- **`React.Children.count`**:  
  Returns the total number of children.

---