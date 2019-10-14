# package android.support.v7.app does not exist - Android

After Androidx release on May 8, 2018. We can see this error on React Native > 0.60. Well, how to solve this problem. Let's look at the error first.

> Note: If you want to learn more thing about Androidx. Follow this [link.](/React-Native/HowToArticles/Androidx.md)

![androidx](/assets/images/android-v4-v7-error.png)

### To solve problem:

#### - Appcompat type
Old usage:
```java
import android.support.v7.app.AlertDialog;
```

New usage:
```java
import androidx.appcompat.app.AlertDialog;
```
<br/>

#### - Core type
Old usage:
```java
import android.support.v7.app.NotificationCompat;
```

New usage:
```java
import androidx.core.app.NotificationCompat;
```

<br/>

#### - Annotation type
Old usage:
```java
import android.support.annotation.Nullable;
```

New usage:
```java
import androidx.annotation.Nullable;
```
