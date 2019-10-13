# AndroidX

## AndroidX Nedir?
AndroidX projesi, Google’ın 2018 yılında piyasaya tanıttığı bir projedir. Bu anlamda, uygulama tasarlayanlar için AndroidX’in yeni bir kavram olduğunu söyleyebiliriz. AndroidX, temel olarak Android tarafından [Jetpack](https://developer.android.com/jetpack) içindeki kütüphaneleri
- geliştirmek,
- test etmek,
- paketlemek,
- sürümlerini hazır hale getirmek,

piyasaya sunmak amacıyla geliştirdiği açık kaynak kodlu bir projedir. En gelişmiş `Jetpack` componentlerini ve `Support Library`’i kapsar, daha gelişmiş halidir diyebiliriz.

![androidx-doc1](/assets/images/androidx-doc1.png)

## Jetpack Nedir?
Jetpack, Android tarafından önerilen google kütüphanesidir, araç(tool)lardan oluşur ve geliştiricilerin daha yüksek kalitede, verimli ve hızlı çalışan programlar yazabilmesine olanak sağlar. Temel olarak 4 kategoriden oluşur:

- Architecture
- Foundation
- UI
- Behavior

Jetpack, AndroidX’in kütüphanelerini API’den ayrı olarak içerir. Böylece Jetpack geriye dönük uyumluluk sağlar ve Jetpack componentlerini en güncel sürümleriyle kullanabilmeyi sağlar.

![android-jetpack](/assets/images/android-jetpack.png)

Jetpack’in neden geliştirildiği ve ne amaçla kullanılabileceğini belirten Android Developers videosu:

[![android-developers](https://img.youtube.com/vi/LmkKFCfmnhQ/0.jpg)](https://youtu.be/LmkKFCfmnhQ)

## AndroidX Neden Geliştirildi ?
Support Library’nin eskimeye başlamasıyla beraber;

Android, `AndroidX`’i piyasaya sürerek 2011 yılında piyasaya sürdüğü, `Support Library`’i geliştirmeyi ve kullanılan kütüphane kavramına yeni bir bakış açısı getirmeyi hedefledi. Bunun temel sebeplerinden biri `Support Library`’nin sürekli olarak geliştirilse de kullanıcının kafasını karıştıran bazı sorunlar içermesiydi. Kullanıcılardan da gelen geri dönüşler doğrultusunda AndroidX geliştirilmiş oldu.

### Support Library’den Farkları Nelerdir ?
- Kütüphaneler, kendilerini kullanabilmek için gerekli olan en düşük API seviyesini belirtir. Buna örnek olarak, `support-v4` kütüphanesini verebiliriz. Burada `“v4”`, kütüphanenin desteklediği _en düşük_ SDK sürümünü 4 olarak gösterir. Fakat güncel SDK sürümüyle olması gereken _en düşük_ `API seviyesi 16’dır`. Kütüphane isimlerinde düzeltilmemiş/geliştirilmemiş olan API seviyeleri zamanla özellikle programcıların kafasını karıştırıyordu.
- Aynı zamanda kütüphane isimleri çok uzuyor ve fazla kütüphane kullanımlarında okumayı zorlaştırıyordu. Bunlarla beraber her bir library için desteklenen (v4,v7,v13..) sürümleri bilmek zorunda kalmak hoş bir durum değildi. `Bu yüzden hepsini destekleyecek olan AndroidX sunuldu`.

Support Library’nin sürümleriyle ilgili StackOverFlow konusu:

https://stackoverflow.com/questions/18271429/difference-between-android-support-v7-appcompat-and-android-support-v4

- Support Library kullanıldığında, kütüphaneler aynı versiyon üzerinde çalışmak zorundadırlar. AndroidX’in gelmesiyle beraber bu bağımlılık ortadan kalkmış durumda.

Örnek olarak:

```java
'com.android.support:support-compat:28.0.0'
'com.android.support:recyclerview-v7:28.0.0'
```

şeklinde kullanılmalı iken,

`AndroidX` ile
```java
'androidx.cardview:cardview:1.0.0' 'androidx.constraintlayout:constraintlayout:1.1.3'
```
şeklinde bir kütüphane kullanımı mümkün olmaktadır.

Böylece, sürekli başımızı ağrıtan

![androidx-error](/assets/images/android-v4-v7-error.png)

hatasından kurtulmuş olacağız.

- Support Library’den farklı olarak, AndroidX kütüphaneleri ayrı ayrı tutulur ve güncellenir.

Son olarak, Support Library’nin son sürümü 28.0.0 iken, AndroidX 1.0.0 sürümüyle yayınlanacaktır.

## AndroidX Nasıl Kullanılır ?
Var olan projemizi AndroidX’e geçirmek için Android biz programcılar için bir kolaylık sağlamış durumda:

`Migrate to AndroidX`

Projemizi AndroidX’e geçirmeden önce yapmamız gereken adımlar bazı adımlar bulunmaktadır.

1. `Build.gradle(Module: app) → compileSdkVersion` (en az) `28` olarak ayarlanmalıdır.

```java
android {
    compileSdkVersion 28
}
````

2. `Tools → DK Manager → Appearance & Behavior → System Settings → Android SDK` ayarlarından API Level’i 28 veya üstü olan SDK(lar) seçilmelidir. Programımızda en az 1 tanesi bulunmalıdır.

![android-api28](/assets/images/android-api28.png)

3. `Android Gradle Build` Version `3.2` veya üstü olarak ayarlanmalıdır.
`build.gradle(Project: ) → dependencies → classpath` ayarları yapılmalıdır.

```java
dependencies {
    classpath 'com.android.tools.build:gradle:3.2.1'
}
```

4. `Gradle Version 4.6` ve `üstü` olmalıdır.
Bu `Gradle Scripts → gradle-wrapper.properties` seçeneğinden ayarlanabilsede, `Ctrl + Shift + Alt + S` kısayolundan veya `File → Project Structure` yolundan da ayarlanabilir.

![Temel Gradle Ayarları](/assets/images/gradle-structure.png)


5. Temel ayarlarımızı yaptıktan sonra, `Refactor → Migrate to AndroidX` seçeneğine tıklayabiliriz.

![Migrate to AndroidX](/assets/images/migrate-file.png)


Bu adımdan sonra Android Studio onayımızı ister. “Back project as Zip file” kısmında isterseniz tik işaretini kaldırabilirsiniz. Burada Android Studio size projenizi zip uzantılı olarak yedeklemek isteyip istemediğinizi sorar. Projeniz ilerlemiş durumda ise yedeklemenizi tavsiye ediyorum.

![Migrate İşleminin Onaylanması](/assets/images/migrate-warn.png)

Onayımız verildikten sonra projemiz ve içindeki kütüphaneler AndroidX kütüphanesine uygun bir şekilde çevrilmiş olacaktır.

AndroidX kütüphanelerinin Support Library karşılığını görmek için:
https://developer.android.com/jetpack/androidx/migrate
linkini inceleyebilirsiniz.

Faydalı olması dileğiyle.

Kaynak: [Muhammed Burak Çakır](https://medium.com/@mburakcakir)
