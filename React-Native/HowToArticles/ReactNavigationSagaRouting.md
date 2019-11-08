# React Navigation Saga Routing

In our react native project. Sometimes, we need to use saga for routing between pages.

For Example: Logout events, project logouts you but you have to route screen to Login screen.

## Solution:

Create a reference for getting navigation moves. And export it globally.

```javascript
// App.js

export let navigatorRef;

export default class App extends Component {

  componentDidMount() {
    navigatorRef = this.navigator;
  }


  render() {
    const map = AppStore.getState();
    return (
      <Root>
        <Provider store={AppStore}>
          <AppContainer
            ref={nav => { this.navigator = nav; }}
          />
        </Provider>
      </Root>
    );
  }
}
```

Inject your navigatorRef to your saga.

```javascript
export function* logoutHandler() {
    const resetAction = StackActions.reset({
      index: 0,
      actions: [NavigationActions.navigate({ routeName: 'Login' })],
    });
    navigatorRef.dispatch(resetAction);
}
```

Thanks to this usage you can send your user to Login screen. Happy Coding <3