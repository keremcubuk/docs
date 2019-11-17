# Firebase Android Integration

In this document, we are going to add firebase to Android app.

First of all, go to [firebase console](https://console.firebase.google.com/). And follow the steps below.

1. In your `Firebase Dashboard` click the `Android Icon` :alien: on Banner. 

    ![firebase-dashboard](firebase-dashboard.png)

2. Complete the inputs and click the `Register App` button.

    ![step-1](step-1.png)

3. Download config file which name is `google-services.json`.

    ![step-2](step-2.png)

4. Add your `google-services.json` file under `yourApp > android > app` folder.

    ![android-path](android-path.png)

5. Add `Firebase SDK` to your app.

    ![step-3](step-3.png)

- Go to `yourApp > android > build.gradle` file.

    ![build-gradle-1](build-gradle-1.png)

    ```java
    buildscript {
        repositories {
            // Check that you have the following line (if not, add it):
            google()  // Google's Maven repository
        }
        dependencies {
            ...
            // Add this line
            classpath 'com.google.gms:google-services:4.3.2'
        }
    }

    allprojects {
        ...
        repositories {
            // Check that you have the following line (if not, add it):
            google()  // Google's Maven repository
            ...
        }
    }
    ```

- Next step of adding SDK. Open `yourApp > android > app > build.gradle` file.

    ![build-gradle-2](build-gradle-2.png)

    ```java
    apply plugin: 'com.android.application'

    dependencies {
    // add the Firebase SDK for Google Analytics
    implementation 'com.google.firebase:firebase-analytics:17.2.0'
    // add SDKs for any other desired Firebase products
    // https://firebase.google.com/docs/android/setup#available-libraries
    }
    ...
    // Add to the bottom of the file
    apply plugin: 'com.google.gms.google-services'
    ```

- After implementation. In your `Android Studio` sync your project.

6. Run your app. After complete the verification click to `Continue to Console` button.

    ![step-4](step-4.png)

7. Your app added to Firebase successfully!

    ![step-5](step-5.png)
