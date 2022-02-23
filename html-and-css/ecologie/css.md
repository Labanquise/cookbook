---
description: Relatif au CSS
---

# 📘 CSS

## SASS / SCSS

Utilisation d'un préprocesseur CSS (comme [SASS](https://sass-lang.com)) permet de palier à certaines fonctionnalités manquantes en CSS. Notamment le nesting de déclaration, l'import ou la dynamisation.

## Appel asynchrone du CSS

Votre feuille de style doit être appelée de manière asynchrone afin de ne pas bloquer le chargement des éléments

La balise `<noscript>` permet de mettre un fallback pour les navigateurs les plus anciens

```html
<link rel="preload" href="<Chemin de votre style.css>" as="style" onload="this.onload=null;this.rel='stylesheet'">
<noscript><link rel="stylesheet" href="<Chemin de votre style.css>"></noscript
```

## Critical CSS

Pour les sites les plus volumineux, il est possible d'utiliser un critical css. Le but consiste à réunir l'ensemble des lignes ne servant qu'à afficher les éléments au dessus de la page de flottaison et/ou récurent : **le header**, **la navigation**, **le footer** (optionnel) ainsi que les premiers éléments de chaque page (ou uniquement de la **homepage**)

Ces styles ne doivent pas être dans un fichier à part en production. La technique consiste à placer cet ensemble de style dans une balise dite "inline" `<style></style>` dans la partie `<head></head>` de votre page.

**Lire aussi :** [https://web.dev/extract-critical-css/](https://web.dev/extract-critical-css/)

## L'utilisation de classe en CSS

Contrairement à ce qu'on pourrait croire les classes ne sont pas "obligatoire". En effet il est fort possible d'atteindre un élément par un chemin simple, son id ou sa position.

Chaque classe rajoute du code en HTML et en CSS, il est donc primordial de réfléchir à leur utilisation et leur nommage, évitez donc les règles de nommage à rallonge comme [**BEM**](https://www.alticreation.com/bem-pour-le-css/)

```html
<!-- CSS en SASS -->
<style>
    header, footer {background-color:#ffccaa}
    #splash {
        p {font-size:0.75rem}
        div span {position:absolute}
    }
</style>

<!-- HTML -->
<html>
    <head>...</head>
    <header>...</header>
    <main>
        <section id="splash">
            <h2>Titre de la section</h2>
            <p>un paragraphe</p>
            <p>un autre paragraphe</p>
            <div>
                <img src="url" width="100" height="100" alt="Description">
                <span>Text en surimpression</span>
            </div>
        </section>
    </main>
    <footer></footer>
</html>
```

Les classes ne doivent servir que quand un style d'élément se **répète souvent** et à peu besoin d'être surcharge : la définition du style de vos **boutons** par exemple.

Il existe désormais tout un tas de sélecteur pour différencier les éléments, en autre :&#x20;

* _**">"**_ : choisit un enfant direct uniquement
* _**"+"**_ : voisin direct
* _**":first-child"**_ et _**":last-child"**_ : permettant de sélectionner le premier/dernier enfant
* _**"x:first-of-type"**_ et _**"x:last-of-type"**_ : permettant de sélectionner le premier/dernier élément de type x
