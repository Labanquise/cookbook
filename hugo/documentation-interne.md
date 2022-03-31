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



## Passer des paramètres à un fichier JS

Etape souvent délicate, le moteur **HUGO** permet d'ajouter facilement dans le **HTML**, mais pas directement dans les assets (comme un **fichier JS**)

Il est possible de passer des données au fichier JS grâce à la commande js.Build et les récupérer après en JS.

### Dans le layout :&#x20;

```html
{{ $tools := resources.Get "/js/tools.js" | resources.Minify | js.Build (dict "params" (dict "config" ($data.Get "config") "companies" ($data.Get "companies" | jsonify)) "format" "esm")}}
<script src="{{ $tools.Permalink }}" type='module' async></script>
```

**js.Build** va prendre en paramètre un dictionnaire (paire clé/valeur) :&#x20;

* **"params"** : les valeurs que vous souhaitez transférer au script js (peut être sous la forme d'un dict)
* **"format"** : valeur utilisé pour le build, je recommande "ESM"

### Dans le script JS :&#x20;

```javascript
import * as params from '@params';
let config = JSON.parse(params.config);
let companies = JSON.parse(params.companies);
```

### Point d'attention

**js.Build** parse l'intégralité du fichier, si une fonction ou variable n'est pas appelée, **js.Build** l'efface du résultat final.

Attention aussi à l'effet de cascade (une première fonction n'est pas appelée, les fonctions appelées uniquement à l'intérieure deviennent à leur tour "inutiles")

Une fonction appelée dans le code HTML sera donc effacée.
