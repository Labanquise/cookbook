---
description: 'Ajout à la documentation officielle : https://gohugo.io/documentation/'
---

# 📑 Documentation interne

## Type, Kind et Layout

Une page a forcément ces deux attributs

* **Type** : par défaut type correspond au nom de la section dans laquelle se trouve le fichier.md\
  _Ex_ : `content/pouet/fichier.md` sera du type `pouet`\
  ``Il peut être surchargé via [front matter](https://gohugo.io/content-management/front-matter/)\
  [https://gohugo.io/content-management/types/](https://gohugo.io/content-management/types/)
* **Kind** : il est définit par Hugo, certains peuvent être désactivés via la configuration `disableKinds`\
  _Liste_ : [https://gohugo.io/templates/section-templates/#page-kinds](https://gohugo.io/templates/section-templates/#page-kinds)\
  _Désactivation_ : [https://gohugo.io/getting-started/configuration/#disablekinds](https://gohugo.io/getting-started/configuration/#disablekinds)

Concernant les layouts du template, selon les informations renseignées :&#x20;

* si on utilise "**type**" (ici blog) dans front matter : `/layouts/blog/single.html`
* si on utilise "**layout**" (ici blog) dans front matter : `/layouts/<type>/blog.html`\
  `<type>` représente le dossier où se situe le fichier.md dans content ou le type issu de front matter
* Par défaut si **type** n'est pas défini dans front matter et que le fichier.md se trouve à la racine de /`content/` : le type est "**page**"\
  Lire : [https://gohugo.io/templates/lookup-order/](https://gohugo.io/templates/lookup-order/)

> **Type**
>
> Is value of `type` if set in front matter, else it is the name of the root section (e.g. “blog”). It will always have a value, so if not set, the value is “page”.



