# Eslint
## Eslint Nedir? ve Neden Kullanıyoruz?
Linting neden kullanıyoruz? sorusunu sorarak konuya giriyorum. Bunun için birkaç sebebimiz var.
Projemizde bir kod kalitesini belli bir seviyenin üzerinde tutmaya çalışıyoruz. Bu sebeple linting kullanıyoruz.
Büyük bir ekip olmamızın gerekliliği olarak hemde developer arkadaşların da projeye hızlı adapte olabilmesini sağlamak için linting kullanıyoruz.
Tek bir konfigürasyon dosyamız olacak, kurallarımızı belirleyeceğiz, kurallara uymayan kod satırları uyarılacak, geliştiren kişi tarafından düzeltilmesi gerektiği bilinecek.
Tüm ekip, burada belirlediğimiz standartlarda kod yazabilecek, böylece potansiyel buglar için de proaktif davranmış olabileceğiz.
EsLint:
Bu işi yapmamızı sağlayacak eklentinin adı.

Kurduktan sonra aşağıdaki ekran görüntüsünde olduğu gibi uyarıları, kodlama yaparken görebileceğiz.

![eslint](/assets/images/eslint-lint.png)


> Önemli Not: Projede ek olarak bir kural daha ekledim. Bu kurala istinaden sayfanızda eslint kurallarına uymayan bir durum söz konusu olduğunuzda kodlarınızı git commit ve git push yapamazsınız.

Özetle;
### Why should I use a linter?
Well, imagine you are in a big team and everyone is using a style of code different, some of the developers are using semicolons and others not. After some time, the code will not have a standard. If I'm not only talking about standard, a linter might help you in potential bugs, like disallow assignment operators in conditional, disallow unreachable code after return, throw, continue, and others.


## Ne işe yaradığıyla ilgili aklında soru işaretleri olan arkadaşlar için birkaç populer cevap daha: 
https://stackoverflow.com/questions/8503559/what-is-linting



Nasıl daha iyi kod yazarım sorusuna cevap arayan arkadaşlar için aşağıdaki okuma listesini paylaşıyorum.
https://github.com/airbnb/javascript
https://github.com/airbnb/javascript/tree/master/react

Yaptığımız bu iş ile ilgili daha detaylı bilgi için kütüphane linklerini paylaşıyorum:
https://eslint.org
https://www.npmjs.com/package/eslint
https://github.com/babel/babel-eslint


Kafası karışanlar ve soru işareti olan arkadaşlara konuyu daha detaylı şekilde anlatabilirim. 😉