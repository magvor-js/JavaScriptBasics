# JavaScriptBasics

## A propos des opérateurs

    on a vu les opération arithmétiques:
    `+` : addition
    `-` : soustraction
    `/` : division
    `*` : multiplication
    `5 + 5` ----> 10
    Elles donnent toutes un nombre

    on a vu l'opération d'assignation
    `=` : assigne
    ex : `var toto = 'truc'`
    On range une valeur donnée à droite dans la broite appelée à gauche

    on a vu l'opération de concaténation
    `+` : concatenation
    `'a' + 'b'` ---> 'ab'
    ce qui determine si on fait une addition ou une concaténation ce sont les valeurs qu'on manipule à gauche et à droite de l'opérateur, si les 2 sont des nombres on additionne, si au moins une des 2 est une string on concatène
    Le résultat est une chaine de caratères

    Il y a les opérations de comparaisons
    `>` : strictement supérieur
    `<` : strictement inférieur
    `>=` : supérieur ou égal
    `<=` : inférieur ou égale
    `===` : strictement égal
    `!==` : strictement différent
    (il existe la version double égale au lieu de triple, qui ne vérifie pas le type, c'est à éviter)
    Le resultat est un booléen
    `5 === 5` ---> `true`
    `5 > 5` ---> `false`
    `3 > 0.5` ---> `true`

    Il y a les opérations logiques
    `&&` : et
    `||` : ou
    `!` : not --> donne l'inverse d'un boolean donné

    Avec `ET` il faut les 2
    `true && true` ---> `true`
    `true && false` ---> `false`
    `false && true` ---> `false`
    `false && false` ---> `false`

    Avec `OU` il faut au moins 1 des 2
    `true || true` ---> `true`
    `true || false` ---> `true`
    `false || true` ---> `true`
    `false || false` ---> `false`
    
    
## Autres
    
    La fonction `prompt()` retourne par défaut une chaine de caractères (string), 
    pour transformer en number, nous utiliserons la fonction:
    `parseInt()` ==> `'prompt()'` en "number"
		
		ex: `parseInt(prompt('quel age tu as ?', 10));`
		le "10" est utilisé pour dire base 10 (utilisé dans 99,99% des cas, 
		"2" pour mettre en binaire... c'est le type de variables. 
		On mettra 10 (type de variables dizaines).
		*PS: il est par défaut en base 10 (MAIS IL FAUT L'ECRIRE car certains
		navigateurs ne l'ont pas par défaut !)*
    
    On peut aussi avoir un flottant: `parseFloat()`
    
    On peut aussi faire une transformation Number("63");
    
    Sinon, pour vérifier quel type est:
    `typeof ();` il retourne soit `string, number ou boolean`
		
    
    Opérateur combiné pour les opérations arithmétiques:
    `+= 1` ou `++` : on augmente de 1
    `-= 1` ou `--` : on diminue de 1
    etc.

## Fonctions (function)
   ``` 
    // je déclare une fonction qui prend 2 paramètres
    // j'écris de recette réutilisable avec 2 ingrédients mystères
function calculator(firstGrade, secondGrade) {
    var moyenne = (firstGrade + secondGrade) / 2;
    alert(moyenne);
}

// j'execute une fonction en passant 2 arguments
// je cuisine ma recette en complétant les valeurs des 2 ingrédients mystères
calculator(5, 10);

calculator(10, 12);

function sayMyAgeIn10Years(age) {
    var newAge = parseInt(age, 10);
    newAge = newAge + 10;
    alert('Dans 10 ans tu auras ' + newAge + ' ans');
}


var user = 'Alexis';
var userAge = 30;

// qu'une valeur soit contenu dans une variable ou pas, ce qu'on passe en argument à une fonction, c'est la valeur
sayMyAgeIn10Years(userAge);

sayMyAgeIn10Years(25);

var currentUserAge = prompt('tu as quel age ?');
sayMyAgeIn10Years(currentUserAge);
```

## Tableaux

    Pour créer un tableau on utilise des crochets: 
    `var prenoms = ["Magomed", "Abdoula", "Djabrail"];`
    `index:           0          1           2`
    
    prenoms[0] contient Magomed
    
    On peut mettre dans les tableaux toutes les valeurs qu'on veut : number, string, boolean, 
    dans l'ordre qu'on veut, comme on veut.
    
    On peut avoir des tableaux dans un tableau, et ainsi de suite...
    
    Pour changer la valeur d'un index dans le tableau:
    prenoms[0]= "notMagomed"; (Magomed sera changé en notMagomed)
    

# DOM

DOM signifie document object model, c'est une représentation sous forme d'arbre du document html qu'on consulte. Cette représentation est disponible sous la forme d'un objet appelé `document` dans nos scripts javascript executés dans le navigateur. 

_Astuce du jour : on peut visualiser cet objet en faisant `console.dir(document)`_ 

Ce document possède des tonnes de propriétés et de méthodes, l'objectif est de pouvoir connaitre le contenu du document qu'on consulte dans les scripts mais aussi de réécrire le contenu html au besoin directement depuis nos scripts

## Cibler un élément du document
- Traverser les propriétés du document
```js
// ici je cible le body dans document, dans lequel je cible le premier enfant (mon main) dans lequel je cible le premier enfant (le h1)
var h1Element = document.body.children[0].children[0];
```

- On peut cibler UN élement par son id
```js
// la valeur retournée est un Element
var h1Element = document.getElementById('gameTitle');
```

- On peut cibler UN élement avec un sélecteur css
```js
// je cible le premier élement qui a la classe coucou et je le mémorise dans une var
var coucouElement = document.querySelector('.coucou');

// on peut avoir n'importe quel sélecteur, je cible le premier li enfant d'un ul avec l'id welcome
var listItemElement = document.querySelector('ul#welcome > li');
// la méthode querySelector existe égalementsur tous les Element donc je peux tout à faire écrire
var linkElement = listItemElement.querySelector('a');
```

- On peut cibler TOUS les élements qui matchent avec un sélecteur css
```js
// j'execute la fonction querySelectorAll, on parle de méthode de document, en lui passant en argument un sélecteur CSS
// la valeur de retour est un ensemble d'élements
var coucouElements = document.querySelectorAll('.coucou');
console.log(coucouElements[0]);
console.log(coucouElements[1]);
```

## Modifier un élement du document
1. On cible l'élement
2. On réassigne la propriété qui nous intéresse
```js
// modifier le contenu textuel d'une balise
h1Element.textContent = 'coucou';
// modifier l'attribut class d'une balise
h1Element.className = 'test';
// je modifie l'attribut id
h1Element.id = 'truc';
// je peux me contenter de lire
console.log(h1Element.id);
// on a aussi accès aux classes via classList qui expose ne plus des méthodes trop pratiques pour manipuler les classes, ici via la méthode add on ajoute la class demandée (sans supprimer les autres)
h1Element.classList.add('test');
// on peut modifier le contenu html
h1Element.innerHTML = '<em>Truc</em>';
// on peut modifier les style, chaque propriété CSS est dispo dans la propriété style, /!\ en camelCase
h1Element.style.backgroundColor = 'red';
```

## Créer un élement
```js
// je crée une toute nouvelle balise div prête à être configurée et insérée
var newDivElement = document.createElement('div');
// on peut crée la balise qu'on veut
var newTitleElement = document.createElement('h1');
```

## Insérer un élement dans le document
```js
// on part d'un parent
var parentElement = document.getElementById('parent');
// on prépare un enfant
var newDivElement = document.createElement('div');
// on lui ajoute un enfant, l'enfant sera placé à la fin du parent
parentElement.appendChild(newDivElement);
```


# Event

## Callback

Un callback c'est une fonction transmise à une 2ème fonction en argument. La 2ème fonction pourra alors décidé d'executer la première quand elle le souhaite

```js
// on peut passer un argument lorsqu'on execute une fonction qui attend un paramètre
function test(param) {
    console.log(param); 
}

test(123); // ---> 123

// de la même manière qu'on peut passer un number, un boolean, un object, une string, ... on peut passer une fonction en argument
function test(param) {
    console.log(param); 
}

test(function() { 
    alert('Coucou');
}); // ---> f() { alert('Coucou') }

// ou via une fonction nommée
function test(param) {
    console.log(param); 
}

function coucou() {
    alert('Coucou');
}

test(coucou); // f() { alert('Coucou') }

// la première fonction peut décider d'executer la fonction qu'elle reçoit en paramètre, c'est le principe
function test(param) {
    console.log(param); 
    param();
}

test(function() {
    alert('Salut');
});

function coucou() {
    alert('Coucou');
}

test(coucou);
```

## Les events

La notions d'événements est une notion propre au développeur front. Les événements sont des choses qui se passent dans le navigateur auquelles on pourra réagir, par exemple : le click sur un bouton, le double click sur un lien, la soumission d'un formulaire, le fait de cocher une checkbox, le fait de survoler une div bien prévise. Il s'agit en fait de réagir aux intéractions de l'utilisateur.

Le navigateur (le logiciel qu'on utilise pour consulter nos pages web) capte les intéractions de l'utilisateur avec la page, ces intéractions peuvent êtres :
- Des actions de la souris (clic, survol)
- Des actions du clavier (appuyer sur une touche)
- Des interactions avec un formlaire (envoi du formulaire)
- ...

Dans nos script nous allons pouvoir réagir à ces événements en faisant ce qu'on veut en réaction. On pourra dire "chaque fois que l'événement clic a lieu sur tel bouton, je réagis en executant une série d'instructions"

## Pour la faire courte 

- Pour ajouter un écouteur, on part d'un élement
- On prépare une fonction qui dit quoi faire quand l'événement a lieu
- On enregistre l'événement sur l'élement
```js
// je cible un élement existant
var element = document.getElementById('test');

// je prépare quoi faire
function sayHello(event) {
    alert('hello');
    console.log(event);
}

// je pose mon écouteur
element.addEventListener('click', sayHello);
// ATTENTION à ne pas mettre les () à la fonction sayHello car sinon elle va être lancée d'office sans attendre eventListener.
```

Ou encore
```js
// je crée un nouvel élement
var newElement = document.createElement('div');

// je pose mon écouteur, ici la fonction est dite anonyme
newElement.addEventListener('mouseenter', function(event) {
    alert('hello');
    console.log(event);
});
```


# Variables

Les variables qu'on crée ont une portée

Une variable définie en dehors d'une fonction est globale et donc accessible partout

Une variable définie dans une fonction est locale et donc accessible uniquement dans la fonction

```js
// variable globale
var toto = 123;

function truc() {
    // variable locale
    var much = 'machin';

    console.log(toto); // 123
    console.log(much); // 'machin'
}

console.log(toto); // 123
console.log(much); // error
```

## let

`let` est un mot clé qui sert à la même chose que `var` c'est à dire créer une "boite" pour y mémoriser une valeur, ça s'utilise pareil

```js
// variable globale
let toto = 123;

function truc() {
    // variable locale
    let much = 'machin';

    console.log(toto); // 123
    console.log(much); // 'machin'
}

console.log(toto); // 123
console.log(much); // error
```

### Différence avec var

`let` possède une portée de block, un block de code (une condition, une boucle, ...)
Une let définie dans un block ne le sera que dans le block

```js
if (3 < 5) {
    let answer = true;
    console.log(answer); // true
}
console.log(answer); // error
```


```js
if (3 < 5) {
    var answer = true;
    console.log(answer); // true
}
console.log(answer); // true
```


## const

`const` est un mot clé qui sert à la même chose que `var` c'est à dire créer une "boite" pour y mémoriser une valeur, ça s'utilise pareil

```js
// variable globale
const toto = 123;

function truc() {
    // variable locale
    const much = 'machin';

    console.log(toto); // 123
    console.log(much); // 'machin'
}

console.log(toto); // 123
console.log(much); // error
```


### Différence avec var

`const` possède une portée de block, un block de code (une condition, une boucle, ...)
Une const définie dans un block ne le sera que dans le block


```js
if (3 < 5) {
    const answer = true;
    console.log(answer); // true
}
console.log(answer); // error
```


```js
if (3 < 5) {
    var answer = true;
    console.log(answer); // true
}
console.log(answer); // true
```

###  Différence avec let

`const` ne peut être réassigné, on parle de constante

```js
const gouter = 'kinder';
console.log(gouter); // kinder
gouter = 'chocapic'; // error
```




/////////////////////////////////////////////////////



# Intro à ES6 (EcmaScript 6 ou EcmaScript 2015)

Avant il y avait ES5, qui est resté la norme pendant pas mal d'année

En 2015 il y a eu un regain d'activité et depuis à date anniversaire tous les ans on a de nouvelles versions de la spécifications.

L'idée c'est que javascript est langage qui peut être parlé légèrement différent ici et là, d'un navigateur à l'autre par exemple

L'idée d'ecmascript est de standardiser la manière dont javascript doit être parlé, c'est un ensemble de règles.

Les navigateurs vont pouvoir suivre ces spécifications pour essayer de tous parler pareil. Les navigateurs vont plus ou moins vite à adopoter ces spécifications. Donc il peut y avoir un décalage entre le moment où le langage évolue et où cette évolution est utilisable dans les navigateurs.

Pour vérifier la compatibilité on peut aller sur https://caniuse.com/

## let / const

CF: ci-dessus

A la différence de var, let et const ont une portée de block

La const ne peut pas être réassigné

Si on prend le partie d'utiliser les fonctionnalités ES6 parce que le support le support nous semble correct on préférera utiliser exclusivement `let` et `const` et pas `var`

- Si ma donnée risque d'être réassigné je pars sur une `let`
- Sinon je pars sur une `const`

## template strings / template literals / Littéraux de gabarits / chaînes de caractère entre magic quotes

Jusqu'à présent pour délimiter une chaîne de caractères on passait par simple ou double quotes
```js
var prenom = 'Alexis';
var nom = "Vincent";
```

Pour concaténer on devait sortir de la chaîne et utiliser l'opérateur +
```js
var presentation = 'Bonjour je suis ' + prenom + ', comment ça va ?';
```

Pour écrire sur plusieurs lignes, c'était compliqué
```js
alert('Bonjour
ça va ?'); // pas ok
alert('Bonjour\nça va ?'); // ok
```

ES6 apporte les magic quotes, `
Le caractère accent grave (Alt GR 7 sur un clavier standard)

```js
const prenom = `Alexis`;
const nom = `Vincent`;
```

On va pouvoir concaténer sans sortir de la chaîne en entourant nos expressions avec ${}
```js
const presentation = `Bonjour je suis ${prenom}, comment ça va`; 
const age = `J'ai ${18 + 12} ans.`
const fullname = `Je m'appelle ${prenom} ${nom}`;
```

En plus on peut mettre des retours à la ligne
```js
alert(`Bonjour
ça va ?`); // ok
```

## les fonctions fléchées

Les fonctions fléchées sont un moyen plus light d'écrire des fonctions, moins verbeux.

Il existe une petite différence entre les fonctions classiques et les fonctions fléchées qu'on ne verra pas aujourd'hui

On connait les déclarations de fonctions
```js
function sayHello(firstName) {
    return `Hello ${firstName}`;
}

sayHello('alexis');
```

On connait les expressions de fonctions
```js
const sayHello = function(firstName) {
    return `Hello ${firstName}`;
};

sayHello('alexis');
```

Les expressions de fonctions peuvent s'écrire en version fléchée
Pour passer en fléchée on enlève le mot function qu'on remplace par une grosse flèche (fat arrow =>) entre les parenthèses des paramètres et le corps de la fonction
```js
const sayHello = (firstName) => {
    return `Hello ${firstName}`;
};

sayHello('alexis');
```

### Cas où l'on a qu'une instruction return

Dans le cas ou la seule instruction présente dans la fonction est un return ON PEUT omettre mes accolades ET le return

```js
const sayHello = (firstName) => `Hello ${firstName}`;
;

sayHello('alexis');
```

### Cas où l'on a qu'un seul paramètre

Dans le cas ou on a **1 seul** paramètre, ON PEUT omettre les parenthèses autour du paramètre

```js
const sayHello = firstName => `Hello ${firstName}`;
;

sayHello('alexis');
```


Si on a 0 et ou plusieurs paramètres on DOIT mettre les parenthèses
```js
const coucou = () => `coucou`;

coucou();

const hello = (firstName, lastName) => `Hello ${firstName} ${lastName}`;
```



## Fonctions fléchées

```js
// dans le cas d'une seule ligne, les accolades ET le return n'est pas obligatoire
const nomFonction = (le paramètre, le paramètre, ...) => `coucou`;

// pour faire appel à cette fonction, comme d'hab
nomFonction();


const hello = (firstName, lastName) => {
`Hello ${firstName} ${lastName}
et ainsi de suite`
};


Dans les objets: 

const objet : {
nomFonction: () => {
	ici ce que doit faire la fonction
},
};
```


## Boucles (for ... of ET for ... in)

for ... of est une boucle qui s'utilise uniquement sur les tableaux (array) => ça récupère l'index
pour les objets, on utilise (for ... in) => ça récupère le nom de la propriété

La boucle `for of` (pour les tableaux !)
```js
const array1 = ['a', 'b', 'c'];

for (const element of array1) {
  console.log(element);
}

// expected output: "a"
// expected output: "b"
// expected output: "c"

```

La boucle `for in` (pour les objets !)

```js
const object = { a: 1, b: 2, c: 3 };

for (const property in object) {
  console.log(`${property}: ${object[property]}`);
}

// expected output:
// "a: 1"
// "b: 2"
// "c: 3"

```
