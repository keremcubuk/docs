# Keyboard Actions (Submit - Next - Before)

Klavye üzerinden inputlar arasında gezinmek için NativeBase.Input'ta bazı eklemeler yaparak klavyenizi özelleştirebilirsiniz.

Buna neden ihtiyacımız var sorusuna cevap ise müşteri isteği doğrultusunda formlar arasında geçiş ve devam butonuna basmadan da bir sonraki adıma geçme doğrultusunda ortaya çıkmıştır.

### Klavye Türleri:

```javascript
keyboardType='numeric'

keyboardType='default'

keyboardType='email-address'

keyboardType='phone-pad'
```

### Return Butonu Türleri:

```javascript
returnKeyType='done'

returnKeyType='next'

returnKeyType='go'

returnKeyType='search'

returnKeyType='send'
```


Sayfada birden fazla input varsa inputlar arası geçiş (tab) için aşağıdaki örneği inceleyebilirsiniz.

> Not: Çalışması için zorunlu olanlar.

```javascript
onSubmitEditing={() => {
  this._inputDesc._root.focus(); 
}}
returnKeyType='next'
blurOnSubmit={false}
```

### Example:

```javascript
<Form>
  <Item floatingLabel>
    <Label>Birinci Input</Label>
    <Input
      onChangeText={(username) => this.username = username}
      onSubmitEditing={() => {
          this._inputDesc._root.focus(); 
      }}
      keyboardType='email-address'
      returnKeyType='next'
      blurOnSubmit={false}
    />
  </Item>
  <Item floatingLabel>
    <Label>İkinci Input</Label>
    <Input
      onChangeText={(password) => this.password = password}
      getRef={(c) => this._inputDesc = c}
      onSubmitEditing={() => this.doLogin()}
      keyboardType='numeric'
      returnKeyType='done'
      blurOnSubmit={false}
    />
  </Item>
  <TouchableOpacity onPress={() => this.goForgotPassword()} style={{ position: 'absolute', bottom: 25, right: 0 }} >
    <Text fontNormal pink>GİRİŞ YAP</Text>
  </TouchableOpacity>
</Form>
```


### Referanslar: 

- https://facebook.github.io/react-native/docs/textinput.html

- https://github.com/GeekyAnts/NativeBase/issues/591#issuecomment-297726645

- https://stackoverflow.com/a/32753780/7626331
