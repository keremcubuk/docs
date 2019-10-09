# ngrok error

## English
While developing React and React Native project, we can see `ngrok` error in Windows and Linux platforms. This error does not allow to `npm i` command in your terminal. When you look at the all forums, you cannot find any solution. Let's look our problem.

![ngrok-error](/assets/images/ngrok-error.png)

#### Solution:
Just run these terminal commands with this order:

```powershell
npm cache clean --force 

npm install --ignore-scripts 

npm install react-native 

react-native link

npm install
```

> Note: Before typing these command, you must kill all active nodes.

<br>
<br>

## Turkish
React ve React Native projelerinin Windows ve Ubuntu makinelerde ngrok yükleme hatası alıyor ve npm install işlemi tamamlanamıyor. Aşağıda gördüğünüz bu hatadan kaynaklı projede npm install işlemi tamamlanamıyor.

![ngrok-error](/assets/images/ngrok-error.png)

#### ÇÖZÜM:

Aşağıdaki komutları sırasıyla çalıştırmanız gerekmektedir. Bu şekilde npm install işlemi yaptığınızda hata almayacaksınız.

```powershell
npm cache clean --force 

npm install --ignore-scripts 

npm install react-native 

react-native link

npm install
```

> Not: Yukarıdaki komutları terminalinizde çalıştırmadan önce, çalışan tüm nodları öldürmelisiniz.