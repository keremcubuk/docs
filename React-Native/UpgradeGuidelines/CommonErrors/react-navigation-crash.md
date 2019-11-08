# React Navigation Release Mode Crash

If you are using react-navigation in your project. You have to follow these instruction. In iOS Release mode, react-native application crash between navigating pages. Possible problems:

https://github.com/kmagiera/react-native-gesture-handler/issues/320

To fix problem:

https://github.com/kmagiera/react-native-gesture-handler/issues/320#issuecomment-461119120

```javascript
import "react-native-gesture-handler"; // Just add the top of index.js(root of project)

import { AppRegistry } from "react-native";

import App from "./src/App";

import { name as appName } from "./app.json";
```