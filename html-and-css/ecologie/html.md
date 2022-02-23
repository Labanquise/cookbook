---
description: Relatif au code HTML
---

# 📙 HTML

## HTML : nombre d'éléments

Le but est de garder un [DOM](https://fr.wikipedia.org/wiki/Document\_Object\_Model) ultraléger et donc avec un petit nombre d'élément. C'est désormais plus simple de le faire grâce aux balises sémantiques et au CSS.

Dans tous les cas, il faudra éviter l'hyper-encapsulation, résultant d'une non réflexion en amont du code.

```html
<html>
    <head></head>
    <body>
        <header></header>
        <main>
            <section id="primary">
                <!-- Hyper-encapsulation -->
                <div> <!-- Trop souvent cette div sert juste pour le placement -->
                    <a href="#"><img src="..." width="" height=""></a>
                    <!-- alors que le placement peut être fait sur le a -->
                </div>
                
                <!-- et donc juste -->
                <a href="#"><img src="..." width="" height=""></a>
            </section>
        </main>
        <footer></footer>
    </body>
</html>
```

## HTML : déclaration de fonts

La déclaration des fonts présentées résulte d'une recherche de performance pour le chargement de font externe. La technique implique aussi du CSS.

Pour le reste de ce chapitre, on utilisera la font **poppins** (version Regular et Bold).

### Déclaration en HTML

```html
<link rel="preload" as="font" href="/fonts/Poppins-Regular.woff2 type=font/woff2" crossorigin>
<link rel="preload" as="font" href="/fonts/Poppins-Bold.woff2 type=font/woff2" crossorigin>
```

* **rel="preload"** : sert à spécifier que cette ressource sera nécessaire pour le rendu de la page et qu'il faudrait la charger au plus tôt
* **as="font"** : indique que nous chargeons une feuille de style
* **crossorigin** : prise en charge des _CORS_

**Lire aussi :**&#x20;

* [https://developer.mozilla.org/fr/docs/Web/HTML/Link\_types/preload](https://developer.mozilla.org/fr/docs/Web/HTML/Link\_types/preload)
* [https://developer.mozilla.org/fr/docs/Web/HTML/Attributes/crossorigin](https://developer.mozilla.org/fr/docs/Web/HTML/Attributes/crossorigin)

### Déclaration en CSS

```scss
@font-face {
    font-family: 'Poppins';
    font-style: normal;
    font-weight: 400;
    font-display: swap;
    src: url('/fonts/Poppins-Regular.woff2') format('woff2');
    unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}

@font-face {
    font-family: 'Poppins';
    font-style: normal;
    font-weight: 700;
    font-display: swap;
    src: url('/fonts/Poppins-Bold.woff2') format('woff2');
    unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}
```

**font-display : swap** => swap donne font-face une période de blocage de zéro seconde et une période d'échange infinie. Cela signifie que le navigateur dessine le texte immédiatement, avec une solution de repli si la font n'est pas chargée, mais qu'il remplace la font dès qu'elle est chargée.
