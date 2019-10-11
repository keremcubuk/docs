# How to Add App Icon to React Native Project
As you konw, Android and iOS icons are very spesific and they have various variations so that when we try to add new icon our project. We have to edit all our icons seperately. If you don't want to waste your time, you should use some application for create an iconset. Let's start to create our new iconset.

We are going to use this icon.

![sample-icon](/assets/images/molecular.png)

### Step 1:
Go to this link:
https://makeappicon.com/

### Step 2:
Drop your icon on toaster icon. As you see below.

![makeappicon](/assets/images/makeappicon.png)

And, website can ask some questions. Please answer them. And download your iconset.

### Step 3: 

And go to your email and download your icons. When you open zip file. You will see 3 or more folder like this.

![icons-folder](/assets/images/icons-folder.png)

### Step 4
Let's start to use our icons in our React Native project.

#### iOS
Open your project in Xcode. And click `YourAppName` on left side. Click on the `Images.xcassets` folder. As you see below.

![xcode-icon](/assets/images/xcode-icon.png)

Drag and drop your icons with specific name and resolutions or you can copy all folder under `yourapp > ios > yourappname > Images.xcassets > AppIcon.appiconset` folder. After that you will see your icons in Xcode.

![xcode-icon](/assets/images/xcode-icon-2.png)

##### Final Result:

![xcode-icon](/assets/images/xcode-icon-3.png)

### Android

