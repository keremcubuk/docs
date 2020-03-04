# Property "Reflect" does not exist react-native hermes

If you see this error after activating hermes. Follow this [link](https://github.com/keremcubuk/react-native-boilerplate/commit/8926f00a954824e34caa3bee991420d380502406). 

It cause from the javascript `Reflect` in the `reducerInjector.js` and `sagaInjector.js` files. For the fix replace `Reflect`'s with the `lodash` "has".

Error: 

```javascript
Reflect.has(store.injectedReducers, key)
```

Fix: 

```javascript
import { has } from 'lodash';

has(store.injectedReducers, key)
```