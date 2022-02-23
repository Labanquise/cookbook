---
description: 'Les points en rapport à l''accessibilité #A11Y'
cover: >-
  https://images.unsplash.com/photo-1633904244276-b57f72c983a6?crop=entropy&cs=srgb&fm=jpg&ixid=MnwxOTcwMjR8MHwxfHNlYXJjaHw4fHxhY2Nlc3NpYmlsaXR5fGVufDB8fHx8MTY0NTYzMjk0OQ&ixlib=rb-1.2.1&q=85
coverY: 0
---

# ♿ Accessibilité

## Contraste

Sur le web il est nécessaire de garder un contraste suffisant entre la couleur de fond et celle de la police (_background color_ et _font / foreground color_), dans un but de lisibilité.

* Le **ratio** est expliqué ici : [https://www.w3.org/TR/WCAG21/#contrast-minimum](https://www.w3.org/TR/WCAG21/#contrast-minimum)
* Il existe des **outils pour tester** les différents cas : [https://coolors.co/contrast-checker/112a46-acc8e5](https://coolors.co/contrast-checker/112a46-acc8e5)

## Focus HTML

### "Tag by destination"

L'arrivée de HTML5 a permis de rajouter de la sémantique dans notre code HTML. Il est aussi important de se rendre compte que les tags ont des usages précis et qu'il est contre productif de les détourner.

* **\<header>** : servira à définir le haut de la page
* **\<ul>** : est une liste
* **\<nav>** : permet de créer des menus de navigation
* **\<section>** : décrit une partie générique de la page ou un groupement
* **\<footer>** : le bas de la page

**Exemple :** \
Si un bouton doit emmener l'utilisateur sur une autre page, il est aberrant de créer un **\<button>** et de faire appel au javascript pour réaliser cette action\
De même la solution de styliser un **\<a>** sous l'apparence d'un bouton en CSS n'est pas non plus une solution.\
La balise sert le but : si vous emmenez notre utilisateur sur une autre page de votre site, c'est un lien, avec l'usage de **\<a>** et le "look" de ces derniers : du texte, généralement souligné.

### Les ID

Ils sont uniques. Point.

### La balise "title" du head

Elle est obligatoire. Point.

## Les attributs "alt" et "title"

Que ce soit l'attribut **alt** sur les images ou le **title** sur les liens, celui-ci n'est pas une redite du fichier ou du nom de la page

```html
<!-- Ne faites pas -->
<img src="pingouin.jpg" alt="pingouin">

<!-- Mais décrivez -->
<img src="pingouin.jpg" alt="Photo d'un pingouin glissant sur la banquise">
```

Pour les liens, il faut le faire surtout quand le texte encapsulé n'est pas parlant

```html
<!-- Ne faites pas -->
Pour lire la documentation, <a href="doc.html" title="doc">clicquez-ici</a>

<!-- Mais décrivez -->
Pour lire la documentation, <a href="doc.html" title="lien permettant de lire la documentation du projet AR400">clicquez-ici</a>
```

## Les titres de type "hx"

Les balises de titre vont de **\<h1>** à \<h6> par ordre d'importance décroissant.

**La balise \<h1> est unique sur chaque page HTML**

L'imbrication des titres est possible de telle sorte que :&#x20;

* Il n'y a qu'un seul **\<h1>**
* Il peut y avoir plusieurs **\<h2>** sous le **\<h1>**
* Il peut y avoir plusieurs **\<h3>** sous un **\<h2>**
* Et ainsi de suite

## Les formulaires

**Dans un monde idéal :** <mark style="color:red;">**ON NE CUSTOMISE PAS LES FORMULAIRES !!!**</mark>

**Dans le monde réel :** les formulaires sont des éléments à part dans le rendu HTML / CSS car considérés comme des éléments systèmes, c'est à dire, liés à l'OS sur lequel le navigateur est exécuté.\
Idéalement il ne faudrait pas les customiser, et surtout utiliser ceux déjà présent : une _liste déroulante_ ou un _date picker_ sont des bons exemples.

### La balise \<label>

Il est important de garder à l'esprit : chaque élément de formulaire doit avoir son propre label associé.

```html
<form id="form"> 
    <label for="lastName">Nom*</label>
    <input type="text" id="lastName" required>
    
    <label for="firstName">Prénom*</label>
    <input type="text"  id="firstName" required>
    
    <label for="email">Adresse email*</label>
    <input type="email" id="email" required>
    
    <label for="tel">Téléphone</label>
    <input type="tel" id="tel">
    
    <label for="message">Message*</label>
    <textarea id="message"></textarea>
    
    <input type="submit" value="Envoyer">
</form>
```
