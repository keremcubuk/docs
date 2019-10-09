# Sticky Button with Keyboard - KeyboardAvoidingWiev

Projede android ve ios özelinde klavye ile ilgili sorunlarmız mevcuttu buna genel bir çözüm bulduk. Kendi sayfalarınızı da bu şekilde uyarlamanız gerekmektedir.

```javascript
<BaseContainer>
  <KeyboardAvoidingView
    style={{flex: 1, backgroundColor: variables.gray}}
    behavior='padding'
    enabled
  >
    <ScrollView>

      <!-- Sayfa içeriğim. Bu kısım sizin ekranınız artık -->
      <Form white>
        <Item last>
          <Input
              placeholder={this.messages.email}
              onChangeText={(mail) => this.mail = mail}
          />
        </Item>
      </Form>
      <!-- Sayfa içeriğim: End -->

    </ScrollView>
    <Button
      text={this.messages.continue}
      onPress={() => this.mailVerificate()}
    />
  </KeyboardAvoidingView>
</BaseContainer>
```

### iPhone X and similar devices

```javascript
import { isIphoneX } from 'react-native-iphone-x-helper';

  <KeyboardAvoidingView
    style={keyboardAvoidingViewStyle}
    behavior="padding"
    keyboardVerticalOffset={this.state.keyboardVerticalOffset}
    enabled
  >
    <!-- Content -->
  </KeyboardAvoidingView>
```

Constructor tanımlamamız gerekiyor:

```javascript
  constructor(props) {
    super(props);
    this.state = {
      keyboardVerticalOffset: isIphoneX() ? 15 : null,
    }
  }
```