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
