# JavaScriptBasics

## A propos des opérateurs

    on a vu les opération arithmétiques:
    + : addition
    - : soustraction
    / : division
    * : multiplication
    5 + 5 ----> 10
    Elles donnent toutes un nombre

    on a vu l'opération d'assignation
    = : assigne
    ex : var toto = 'truc'
    On range une valeur donnée à droite dans la broite appelée à gauche

    on a vu l'opération de concaténation
    + : concatenation
    'a' + 'b' ---> 'ab'
    ce qui determine si on fait une addition ou une concaténation ce sont les valeurs qu'on manipule à gauche et à droite de l'opérateur, si les 2 sont des nombres on additionne, si au moins une des 2 est une string on concatène
    Le résultat est une chaine de caratères

    Il y a les opérations de comparaisons
    > : strictement supérieur
    < : strictement inférieur
    >= : supérieur ou égal
    <= : inférieur ou égale
    === : strictement égal
    !== : strictement différent
    (il existe la version double égale au lieu de triple, qui ne vérifie pas le type, c'est à éviter)
    Le resultat est un booléen
    5 === 5 ---> true
    5 > 5 ---> false
    3 > 0.5 ---> true

    Il y a les opérations logiques
    && : et
    || : ou
    ! : not --> donne l'inverse d'un boolean donné

    Avec ET il faut les 2
    true && true ---> true
    true && false ---> false
    false && true ---> false
    false && false ---> false

    Avec OU il faut au moins 1 des 2
    true || true ---> true
    true || false ---> true
    false || true ---> true
    false || false ---> false
    
    
## Autres
    
    La fonction prompt() retourne par défaut une chaine de caractères (string), 
    pour transformer en number, nous utiliserons la fonction:
    parseInt() ==> 'prompt()' en "number"
		
		ex: parseInt(prompt('quel age tu as ?', 10));
		le "10" est utilisé pour dire base 10 (utilisé dans 99,99% des cas, 
		"2" pour mettre en binaire... c'est le type de variables. 
		On mettra 10 (type de variables dizaines).
		*PS: il est par défaut en base 10 (MAIS IL FAUT L'ECRIRE car certains
		navigateurs ne l'ont pas par défaut !)*
    
    On peut aussi avoir un flottant: parseFloat()
    
    On peut aussi faire une transformation Number("63");
    
    Sinon, pour vérifier quel type est:
    typeof (); il retourne soit string, number ou boolean
		
    
    Opérateur combiné pour les opérations arithmétiques:
    += 1 ou ++ : on augmente de 1
    -= 1 ou -- : on diminue de 1
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
    var prenoms = ["Magomed", "Abdoula", "Djabrail"];
    index:           0          1           2
    
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

