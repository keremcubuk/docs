# Multilanguage with React

Proje üzerinde çalışırken oluşturduğumuz componentlerin `messages.js` dosyalarına eklediğimiz `defaultMessage`'lar sadece çeviri olmadığında görünecek textlerdir. 

> Bu sebeple İngilizce ve Fransızca çevirileri ayırt edemeyeceğiz. 🙄

```javascript
  // messages.js
  header: {
    id: 'app.components.CompetitionInstaPosts.header',
    defaultMessage: 'Competitions Top Instagram Posts',
  },
```

Normal şartlarda messages.js dosyasında değişiklik yapmanız durumunda `npm run extract-intl` komutunu çalıştırmanız gerekmektedir. Bu komutu çalıştırdığımız andan itibaren dil dosyaları id'lere göre maplenir. Ve otomatik olarak `en.json` ve `fr.json` dosyalarını güncellemiş olursunuz. 

```javascript
 // en.json
  "app.components.CompetitionInstaPosts.header": "Competitions Top Instagram Posts",
 // fr.json
 "app.components.CompetitionInstaPosts.header": "Partage Instagram des tendances des concurrents",
```

Daha sonra değiştirmeniz gereken kısımları json dosyaları üzerinde yapmanız yeterli olacaktır. (`Id` ve `defaultMessage` değişecekse `messages.js` dosyalarını da güncellemek gerekecektir)

```javascript
  // index.js üzerinde kullanımı
  import { FormattedMessage } from 'react-intl';
  import messages from './messages';

  render() {
    return (
      <FormattedMessage {...messages.header} />
    );
  }
```

Konu ile ilgili react i18n kullanımı:
- https://github.com/react-boilerplate/react-boilerplate/blob/master/docs/js/i18n.md

Konu ile ilgili makale ve örnekler:
- https://medium.freecodecamp.org/setting-up-internationalization-in-react-from-start-to-finish-6cb94a7af725
- https://medium.com/@marcelmokos/internationalize-react-apps-done-right-using-react-intl-library-82978dbe175e
- https://medium.freecodecamp.org/internationalization-in-react-7264738274a0
