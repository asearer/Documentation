**React Native methods** and APIs relevant to general app development, organized by category.

### 1. **Core Components**
These are the primary building blocks of a React Native application.

- **`<View>`**: Container component for layouts and UI elements.
- **`<Text>`**: Displays text.
- **`<Image>`**: Renders images.
- **`<ScrollView>`**: Scrollable container.
- **`<FlatList>`**: Efficient list view for large datasets.
- **`<SectionList>`**: List component that supports sections and headers.
- **`<TextInput>`**: For input fields like textboxes.
- **`<TouchableOpacity>`**: Pressable component with fade-out animation.
- **`<TouchableHighlight>`**: Pressable with highlight effect.
- **`<TouchableNativeFeedback>`**: Touchable using platform-native feedback (Android only).
- **`<Button>`**: Simple button component.
- **`<Switch>`**: Toggle switch component.
- **`<ActivityIndicator>`**: Circular loading spinner.
- **`<Picker>`**: Dropdown picker (deprecated, moved to `@react-native-picker/picker`).

### 2. **Layout & Styling**
React Native uses a **flexbox layout** model and offers styles similar to CSS:

- **`StyleSheet.create`**: Defines a style object for use in components.
- **`flexDirection`**: Row or column arrangement.
- **`justifyContent`**: Aligns items along the main axis.
- **`alignItems`**: Aligns items along the cross axis.
- **`padding`**: Sets padding inside elements.
- **`margin`**: Sets margin outside elements.
- **`position`**: Absolute or relative positioning.
- **`Dimensions`**: Access the device's width and height.
- **`PixelRatio`**: Interacts with the device’s pixel density.

### 3. **Navigation**
React Native itself doesn't come with navigation out of the box, but the following libraries are common:

- **`react-navigation`**: For stack, tab, and drawer navigation.
  - `createStackNavigator()`
  - `createBottomTabNavigator()`
  - `createDrawerNavigator()`
  - `NavigationContainer()`
  - `useNavigation()` – Hook to navigate programmatically.
  - `useRoute()` – Access the current route’s params.

### 4. **Handling User Input**
These methods help to capture and manage user inputs:

- **`onPress`**: Used with buttons or touchable components.
- **`onChangeText`**: Used with `<TextInput>` to handle text change.
- **`onFocus`**: Triggered when input gets focus.
- **`onBlur`**: Triggered when input loses focus.
- **`Keyboard.dismiss()`**: Dismisses the keyboard.

### 5. **State & Lifecycle Methods**
React Native uses the same lifecycle methods as React for class components and hooks for function components.

#### Class Component Lifecycle:
- **`componentDidMount`**: Called after the component is mounted.
- **`componentDidUpdate`**: Called after a component update.
- **`componentWillUnmount`**: Called right before a component is destroyed.

#### Hooks for Functional Components:
- **`useState()`**: State management in functional components.
- **`useEffect()`**: Side-effects and lifecycle events in functional components.
- **`useRef()`**: Create a reference to an element.
- **`useContext()`**: Access context API.

### 6. **Networking**
React Native provides two primary ways to make network requests:

- **`fetch()`**: Built-in for making HTTP requests (GET, POST, etc.).
- **`Axios`** (third-party library): For more advanced networking, promises, and request/response interceptors.
- **WebSockets**:
  - `WebSocket()` constructor to connect to a WebSocket server.

### 7. **Storage**
For persisting data locally on the device.

- **`AsyncStorage`**: Simple, unencrypted, asynchronous key-value storage.
  - `AsyncStorage.getItem(key)`
  - `AsyncStorage.setItem(key, value)`
  - `AsyncStorage.removeItem(key)`
  - `AsyncStorage.clear()`

- **`SecureStore`** (Expo): For storing sensitive data.
- **`MMKV`** (react-native-mmkv): Fast storage solution for React Native.
  
### 8. **Device APIs & Native Modules**
React Native provides several APIs to interact with native device functionalities.

#### **Camera & Media**
- **`CameraRoll`**: Access the device’s camera roll (deprecated, replaced by third-party packages).
- **`react-native-image-picker`**: Capture images and videos.
- **`react-native-camera`**: More extensive camera functionalities.

#### **Location**
- **`Geolocation`**: Access the device's GPS/location data.
  - `Geolocation.getCurrentPosition(successCallback, errorCallback, options)`
  - `Geolocation.watchPosition(successCallback, errorCallback, options)`

#### **Vibration**
- **`Vibration.vibrate()`**: Trigger the device’s vibration.

#### **Battery**
- **`react-native-battery`**: For battery status and charging.

#### **Permissions**
- **`PermissionsAndroid`**: Request runtime permissions on Android.
  - `PermissionsAndroid.request()`
  - `PermissionsAndroid.check()`
  - `PermissionsAndroid.RESULTS.GRANTED`
  - `PermissionsAndroid.RESULTS.DENIED`

#### **Clipboard**
- **`Clipboard`**: Interact with the clipboard (copy/paste).
  - `Clipboard.setString()`
  - `Clipboard.getString()`

#### **Notifications**
- **`react-native-push-notification`**: Handle push notifications.
- **`react-native-notifications`**: For both local and push notifications.

#### **Haptic Feedback**
- **`react-native-haptic-feedback`**: Trigger haptic feedback on supported devices.

### 9. **Animations**
React Native supports basic and advanced animations.

#### **Basic Animations:**
- **`LayoutAnimation`**: Simple layout changes with automatic animations.
  - `LayoutAnimation.configureNext()`
  - `LayoutAnimation.spring()`
- **`Animated`**: More complex animations.
  - `Animated.timing()`
  - `Animated.spring()`
  - `Animated.parallel()` (run animations simultaneously).
  - `Animated.sequence()` (run animations sequentially).
  - `Animated.Value()` – Tracks values for animations.

### 10. **Gestures**
React Native has built-in touchable components, but for more advanced gestures, you might use:

- **`react-native-gesture-handler`**: For handling complex gestures like swipes, pans, taps, etc.
  - `TapGestureHandler`
  - `PanGestureHandler`
  - `ScrollViewGestureHandler`
  - `GestureDetector` (in `react-native-reanimated 2.x` for gesture control).

### 11. **Performance Optimization**
- **`useMemo()`**: Memoizes expensive calculations.
- **`useCallback()`**: Memoizes functions to avoid re-creation.
- **`useEffect()` with dependency arrays: To limit unnecessary re-renders.
- **`shouldComponentUpdate()`**: Class component optimization for rendering.

### 12. **React Native CLI Methods**
Useful for developers working with the React Native CLI:

- **`react-native run-android`**: Runs the app on an Android emulator/device.
- **`react-native run-ios`**: Runs the app on an iOS simulator.
- **`react-native start`**: Starts the Metro Bundler.
- **`react-native link`**: Links native dependencies (used for some libraries).
- **`react-native init`**: Initializes a new React Native project.

### 13. **Debugging & Error Handling**
- **`console.log()`**: Basic logging for debugging.
- **`console.warn()`**: Issues warnings.
- **`console.error()`**: Logs errors.
- **React Native Debugger**: A desktop app for debugging with DevTools.
- **Flipper**: A debugging platform for React Native with plugins for logs, network, and performance.
  
### 14. **Third-party Libraries**
React Native has a rich ecosystem of third-party libraries, here are some common ones:

- **`react-native-vector-icons`**: For using icon sets like FontAwesome.
- **`react-native-reanimated`**: Advanced animations.
- **`react-native-paper`**: UI library with Material Design components.
- **`react-native-maps`**: Integrating Google Maps into your app.

---