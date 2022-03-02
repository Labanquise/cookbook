# 🕹 Astuce

## Destructuring objects <a href="#destructuring-objects" id="destructuring-objects"></a>

{ \*\*\* } permet de récupérer directement la clé "style" \*\*\*

```javascript
const { display } = window.getComputedStyle(document.getElementById('res-ei'));
```

```javascript
// What you write
let { firstName, lastName } = Zell

// ES6 does this automatically
let firstName = Zell.firstName
let lastName = Zell.lastName
```

## Double Equals

Il  est possible d'affecter un booléen en le comparant sur une même ligne

```java
const mobile = display == 'none';
//Si display est à 'none', alors mobile vaut TRUE
```

## DOMContentLoaded

C'est un évènement s'exécutant une fois que le DOM est complétement loadé (pas de "hard code")

## Not Not (qui est là ? :smile:)

La notation !! va permettre de cast un "vrai" booléen sur une valeur

```javascript
const url2Test = document.getElementById('url2test');
// Si l'élement 'url2test' existes
if (!!url2Test) {
  //Some code
}
```

## dispatchEvent

C'est le "vrai" évènement qui est dispatché

```javascript
object.dispatchEvent(new Event('click'))
//Pas de "simulation de click" mais un réel évènement dispatché de façon synchroneva
```

{% embed url="https://developer.mozilla.org/fr/docs/Web/API/EventTarget/dispatchEvent" %}
Documentation officielle
{% endembed %}

## Arrow function

Le système avec le mot clé function n'est plus utilisé on y préfère la arrow function

```javascript
const contentToggle = () => {
    document.getElementById('moreInfo').classList.toggle('hidden');
}
```

{% embed url="https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Functions/Arrow_functions" %}
Documentation officielle
{% endembed %}

## Await simplifié

Utilisation du mot clé await directement dans l'appel de function

```javascript
let data = await getScores(url);
getPepper(data);

//Simplifié en
getPepper(await getScores(url));
```

La logique AWAIT FETCH THEN CATCH linéaire peut s'écrire :&#x20;

```javascript
try {
  wait fetch("http://mybank.com");
} catch(e) {
  throw e;
}
```

## Concaténation et string

Afin d'utiliser la valeur d'une variable dans une chaine on utilisera les \`\`

```javascript
//suffix et elt étant des variables
const resItem = `res${suffix}-${elt}`;
```

Il est aussi possible de le faire en passant n arguments

```javascript
//la concaténation se faite en utilisant des , entre chaque élément
console.log('Pepper Index :', score, 'et', grade);
```

## Let ou Const ?

Si une variable s'utilise dans un scope fermé et ne se modifie pas => const

## findIndex

Renvoie le premier élément remplissant la condition, sinon -1

```javascript
const index = grades.findIndex(({max}) => score >= max);
```

{% embed url="https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex" %}
Documentation officielle
{% endembed %}

## Ecriture ternaire

L'écriture ternaire en JS => condition ? true : false;

```javascript
// Si index n'est pas égal à -1, renvoie grades[index].grade, sinon renvoie 'E'
return index !== -1 ? grades[index].grade : 'E';
```

Il est possible de chainer les écriture ternaires, une valeur (true/false) d'un premier test peut être un autre test ternaire

```javascript
const { color, colorHex } = score >= 75 ? {color: 'green', colorHex: '#1CAF9C'} :
        score >= 25 ? {color: 'orange', colorHex: '#F4AB00'} :
            { color: 'red', colorHex: '#C8222C'};
```

## URLSearchParams

Objet prévu pour la construction d'url pour GET

{% embed url="https://developer.mozilla.org/fr/docs/Web/API/URLSearchParams" %}
Documentation Officielle
{% endembed %}

## Syntaxe de décomposition

Va permettre notamment de merge un object

```javascript
const metadata = {...enterprise, ...optin};
```

{% embed url="https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Operators/Spread_syntax" %}
Documentation officielle
{% endembed %}
