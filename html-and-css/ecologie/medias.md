---
description: Relatif aux médias (images, vidéos, etc...)
---

# 🖼 Medias

## Médias : formats, crunch

Il faut savoir choisir le format le plus adapté, en connaissant les contraintes de chaque extension :&#x20;

* **GIF** : 256 couleur, une transparence à 1 niveau (oui/non)
* **JPG** : bonne compression, mais attention aux artefacts, pas de transparence
* **PNG** : qualité préservée, transparence multi-niveau, mais attention au poids

### Webp ?

Format spécifiquement développé pour le web, il va permettre de réduire drastiquement le poids tout en préservant la qualité visuel : attention, le format n'est pas encore 100% supporté.

![Support à date : 31/03/2022 (Caniuse)](<../../.gitbook/assets/2022-03-31 11\_28\_44-\_webp\_ \_ Can I use... Support tables for HTML5, CSS3, etc.png>)

### Compress ou Crunch ?

* **Compresser** : cela va consister à appliquer un algorithme permettant d'encoder l'image et ainsi réduire son poids. C'est un travail graphique.
* **Cruncher** : on va venir se débarrasser des métadonnées inutiles pour une image, c'est un travail textuel.
* **Squoosh** : outil permettant la compression/crunch en ligne \[[Lien](https://squoosh.app)]

## Médias : images vectorielles

Les images vectorielles ne sont pas représentés par des pixels, mais par des lignes et forme définie par des coordonnées.

Ces images peuvent ainsi être redimensionnée quasi-infiniment sans perte de qualité et d'intégrité.

Le format le plus connu pour le web à ce jour est le **SVG**.

* **Fichier** : il est possible d'utiliser l'image "normalement" avec une balise IMG et l'extension .svg\
  Il est possible de cruncher un fichier SVG \[[Crunch SVG](https://vecta.io/nano)]
* **CSS** : le fichier peut être transformé pour l'utilisé dans une feuille de style CSS. \[[Outil permettant la transcription SVG => CSS](https://yoksel.github.io/url-encoder/)]
* **HTML** : il est possible d'utiliser le SVG directement dans le code HTML. <mark style="color:red;">**Mais attention : celui-ci va créer de nombreux nœuds DOM si votre image est complexe !**</mark>

## Et les vidéos ?

Pour le moment, la meilleure recommandation c'est de les éviter 😁. Mais si vous ne pouvez pas, garder ceci en tête :&#x20;

* Eviter les vidéos qui démarrent automatiquement sans le consentement de l'utilisateur
* Si vous pouvez préférez une image, qui redirigera par la suite vers la vidéo, ainsi intitule de la précharger dans le code pour les utilisateurs n'en ayant pas besoin.
