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
