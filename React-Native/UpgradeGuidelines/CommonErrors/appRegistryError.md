# appRegistry Error
 
If you see this error, `Module AppRegistry is not registered callable module (calling runApplication)` follow the instruction.

![error](https://user-images.githubusercontent.com/5610758/66041369-fe020880-e519-11e9-8616-58da88177c0f.png)

When you rebuild you can see this error:

![Image](https://user-images.githubusercontent.com/5610758/66043899-ac10b100-e520-11e9-87b1-ad59b9469bda.png)


## Solution

1. Check your libraries `react-native` dependencies.

If you see differences with your library version, you can take this error. Because, react-native only works with compatible versions.

```js
// myapp package.json

   dependencies: {
      react-native: 61.1.3,
   }

```

```js
   // my child library package.json

   dependencies: {
      react-native: 59.1.0,

     //  This version must be same with myapp react-native version
   }

```

2. Clean your cache and rebuild your project.

```shell
npm start -- --reset-cache
```
