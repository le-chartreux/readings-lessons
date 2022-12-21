# Coder Proprement - leçons

Ensemble des enseignements que j'ai tirés du livre *Coder Proprement* par **Robert C. Martin**

## Préface

- *Dieu est dans les détails* a dit Ludwig Mies van der Rohe.
- Les petits riens d'une construction négligée, comme une porte qui ferme mal, annulent totalement le charme de l'ensemble. C'est toute l'idée du code propre.
- La TPM (*Total Productive Maintenance*) est une approche qualité japonaise qui se focalise sur la maintenance. Le but est ici de détecter les bugs avant qu'ils ne se produisent. Elle s'appuie sur cinq principes, les **5S** :
  - **Seiri** (*organisation*) : savoir où se trouvent les choses → important de bien nommer et documenter.
  - **Seiton** (*ordre*) : le code doit se trouver là où on s'attend à le trouver.
  - **Seiso** (*nettoyage*) : pas de commentaires inutiles, pas d'ancien code mit en commentaire.
  - **Seiketsu** (*propre*) : le code est standardisé.
  - **Shutsuke** (*éducation*) : suivre les pratiques et réfléchir au travail des autres, évoluer.
- Le manque d'assiduité finit par être couteux : *un assassin revient toujours sur les lieux du crime*.

## Chapitre 1 - Code propre

- Le temps où les directeurs de projet génèreront du code à partir des spécifications n'arrivera pas. Il y aura toujours du code, car il représente les détails des exigences. Pour se passer de code, il faudrait que les exigences soient parfaites. Or une exigence parfaitement explicitée est un code avec un haut niveau d'abstraction : elle est rigoureuse, précise, et tellement formelle et détaillée qu'une machine pourra la comprendre et l'exécuter. (p.2)
- Vous ne respectez pas les échéances en travaillant mal. La seule manière de respecter le planning, ou d'aller vite, est de garder en permanence le code aussi propre que possible. (p.7)
- Il est extrêmement complexe, voir impossible, d'écrire un code qui dès son premier jet appliquera tous les principes. C'est tout à fait normal : il faut d'abord écrire quelque chose de fonctionnel, puis l'améliorer. (p.55)

### Qu'est-ce qu'un code propre ?

- Différentes citations de programmeurs parmi les plus influents pour répondre à cette question :

>J'aime que mon code soit élégant et efficace. La logique doit être simple pour que les bogues aient du mal à se cacher. Les dépendances doivent être minimes afin de faciliter la maintenance. La gestion des erreurs doit être totale, conformément à une stratégie articulée. Les performances doivent être proches de l'idéal afin que personne ne soit tenté d'apporter des optimisations éhontées qui dégraderaient le code. Un code propre fait une chose et la fait bien.  
-- Bjarne Stroustrup, inventeur du C++

> Un code propre est un code simple et direct. Il se lit comme une prose parfaitement écrite. Un code propre ne cache jamais les intentions du concepteur, mais est au contraire constitué d'abstractions nettes et de lignes de contrôle franches.  
-- Grady Booch, auteur du livre Object Oriented Analysis and Design with Applications.

> Un code peut être lu et amélioré par un développeur autre que l'auteur d'origine. Il dispose de tests unitaires et de tests de recette. Il utilise des noms significatifs. Il propose une manière, non plusieurs, de réaliser une chose. Ses dépendances sont minimales, et explicitement définies. Il fournit une API claire et minimale. Un code doit être litteraire, puisque, selon le langage, les informations nécessaires ne peuvent pas toutes être exprimées clairement par le seul code.  
-- Dave Thomas, fondateur d'OTI, parrain de la stratégie d'Eclispe.

> Je pourrais établir la liste de toutes les qualités que j'ai notées dans un code propre, mais l'une d'elles surpasse toutes les autres. Un code propre semble toujours avoir été écrit par quelqu'un de soigné. Rien ne permet de l'améliorer de façon évidente. Tout a déjà été réfléchit par l'auteur du code et, si vous tentez d'imaginer des améliorations, vous revenez au point de départ, en appréciant le code qu'on vous a laissé - un code laissé par quelqu'un qui se souciait énormément de son métier.  
-- Michael Feathers, auteur de Working Effictively with Legacy Code

> Par ordre de priorité, un code simple :  
    - passe tous les tests  
    - n'est pas redondant  
    - exprime toutes les idées de conception présentes dans le système  
    - minimise le nombre d'entités, comme les classes, les méthodes, les fonctions et assimilées  
[...] Lorsque la même chose se répète de nombreuses fois, cela signifie que l'une de nos idées n'est pas parfaitement représentée dans le code. [...] Si un objet ou une méthode a plusieurs rôles, le décomposer [...] Il faut abstraire les fonctionnements [...]  
-- Ron Jeffries, auteur de Extreme Programming Installed et de Extreme Programming Adventures in C#

> Vous savez que vous travaillez avec du code propre lorsque chaque méthode que vous lisez correspond presque parfaitement à ce que vous attendiez. Vous pouvez le qualifier de beau code lorsqu'il fait penser que le langage était adapté au problème.  
-- Ward Cunningham, co-inventeur de l'eXtreme Programming

--> Ce n'est pas le langage qui fait que le programme apparaît simple. C'est le programmeur qui fait que le langage semble simple.
(p.8 à 14)

- Nous lisons *constamment* l'ancien code pour écrire le nouveau. De ce fait, en rendant un code facile à lire, on le rend plus facile à écrire. (p.16)

## Chapitre 2 : Noms significatifs

- Les noms sont omniprésents : il est donc préférable de bien les choisir. (p.19)
- Choisir les bons noms prend du temps, mais permet d'en gagner plus encore. (p.20)

### Choisir des noms révélateurs des intentions

- Le nom d'une variable, d'une fonction ou d'une classe doit répondre à certaines grandes questions : la raison de son existence, son rôle et son utilisation. (p.20)
- Si un nom exige un commentaire, c'est qu'il ne répond pas aux questions ci-dessus. (p.20)

### Éviter la désinformation

- Ne pas utiliser des variables avec des noms trop proches les uns des autres. (p.22)
- Ne jamais nommer une variable `l` ou `O` (à cause de la ressemblance avec `1` et `0`). (p.22)

### Faire des distinctions significatives

- Ne jamais préfixer (ou suffixer) un nom pour le différencier d'un autre : si ce ne sont pas les mêmes éléments, il n'y a pas de bonne raison qu'ils aient un nom semblable. Cela ne fera que créer de la confusion pour savoir lequel utiliser. Exemples : `object` décliné en `the_object`, `object_1`,  `objekt`, `an_object`, `object_var`, `object_data`, `object_info`, `object_object`... (p.23 à 24)

### Choisir des noms prononçables

- Le fait qu'un nom soit imprononçable est un indicateur de mauvais nommage. (p.24-25)

### Choisir des noms compatibles avec une recherche

- Les noms trop courts (par exemple `e`) sont complexes à rechercher : ils donneront énormément de résultats, car seront des sous-ensembles d'autres noms. (p.25)

### Éviter la codification

- Ne pas inclure le type d'une variable dans son nom : une liste de comptes s'appellera `accounts` et non pas `account_list`. (p.26)
- Ne pas signaler les interfaces puisque cela n'est pas important pour l'utilisateur. Au besoin, signaler l'implémentation : `element` et `element_implementation` plutôt que `element_interface` et `element`. (p.28)

### Éviter les associations mentales

- Le lecteur ne doit pas avoir à convertir mentalement les noms en signification : il ne doit pas avoir à se dire "OK, dans ce code, à chaque fois que je vois `dc` cela signifie `description`". (p.28)
- Pas de nom sur un seul caractère, excepté ceux de compteur de boucle `i`, `j`, `k` (mais jamais `l`, cf [Eviter la désinformation](#éviter-la-désinformation)) : ils seront forcément à convertir en signification. (p.28)

### Noms des classes

- Les noms de classes et d'objets doivent être des noms ou des groupes nominaux, jamais des verbes ; e.g. `Customer` et `AdressParser`. (p.28)
- Il faut éviter les préfixes et suffixes comme `Manager`, `Processor`, `Data` ou `Info`. En effet, ces termes sont inutiles, voir confus dans le cas ou une classe sans ce terme existe. E.g, quelle est la différence entre  ̀User` et `UserData` ? Il n'y en a pas, puisque `User` est déjà un ensemble d'informations sur un utilisateur. (p.28)

### Noms des méthodes

- Les noms de méthodes doivent être des verbes ou des groupes verbaux ; e.g. `save` et `delete_page`. (p.29)
- Les accesseurs, mutateurs et prédicats doivent être nommés d'après leur valeur et préfixés par `get`, `set` ou `is` ; e.g. `employee.get_name()`, `customer.set_name("mike")` ou `if paycheck.is_posted(): ...` (p.29)
- Lorsque les constructeurs sont surchargés, nous devons utiliser des méthodes de fabrique statique avec des noms qui décrivent les arguments ; e.g. `Complex.from_read_number(23.3)` est généralement préférable à `Complex(23.3)`. (p.29)

### Choisir un mot par concept

- Choisissez un mot par concept et restez-y fidèle : ne pas avoir `controller`, `manager` et `driver`. (p.30)

## Chapitre 3 : Fonctions

### Faire court

- Plus une fonction est courte, plus elle est compréhensible et maintenable. Les fonctions doivent faire de préférence entre 5 et 10 lignes, et rarement dépasser 20 lignes. (p.38)
- Le contenu des instructions bloc (`if`, `while`, `for`, etc.) ne doivent occuper qu'une ligne, qui sera probablement un appel de fonction. Cela permet de garder la fonction englobante courte, mais également d'ajouter une valeur documentaire, car la fonction appelée aura un nom parfaitement descriptif. (p.39)
- Pas de structures imbriquées : le niveau d'indentation doit être inférieur ou égal à 2. (p.39)

### Faire une seule chose

- Une fonction ne doit faire qu'une seule chose. Elle doit la faire bien et ne faire qu'elle. (p.40)
- Si d'une fonction, on ne peut extraire que des fonctions dont le nom est une reformulation de son implémentation (e.g. transformer `if cond then func_a(param)` en `func_a_if_cond(param, cond)`), elle ne fait qu'une chose. (p.40)
- Une fonction qui ne fait qu'une seule chose ne peut pas être décomposée en sections. (p.41)
- Si faire deux choses est déjà problématique, faire deux choses en annonçant n'en faire qu'une est grave. Les effets secondaires sont à proscrire absolument, e.g. 
  ```python
  def can_vote(user: User) -> bool:
      user.address = "Canada"  # NON, on ne s'attend pas à ce que can_vote modifie l'adresse !
      return user.age > 18
  ```
  (p.49-50)

### Un niveau d'abstraction par fonction

- Une fonction qui ne fait qu'une seule chose ne contient que des instructions au même niveau d'abstraction. (p.41)
- Règle de la décroissance (*Stepdown Rule*) : un code se lit de haut en bas, chaque fonction est suivie d'une de niveau d'abstraction égal ou inférieur. Nous voulons que le code puisse se lire comme un ensemble de paragraphes `POUR`, chacun décrivant le niveau d'abstraction actuel et faisant référence à des `POUR` plus bas. E.g. : 
  - POUR cuisiner des pâtes, préparer la casserole, faire cuire les pâtes dans la casserole, égoutter les pâtes.
  - POUR préparer la casserole, remplir la casserole d'eau, ajouter du sel, mettre la casserole sur la plaque, allumer la plaque et attendre jusqu'à ce que l'eau bouille.
  - POUR remplir la casserole d'eau, mettre la casserole dans l'évier, ouvrir le robinet, laisser l'eau couler jusqu'à ce que la casserole soit remplie, fermer le robinet.
  - POUR mettre la casserole dans l'évier, [...]
  - [...]
  - POUR faire cuire les pâtes dans la casserole, ajouter les pâtes dans la casserole, régler la puissance de la plaque à 3/4 de sa puissance et attendre 7 minutes.
  - [...]
  - POUR égoutter les pâtes, mettre l'égouttoir dans l'évier et verser les pâtes dedans.
  - [...]
(p.41)

### Conditions sur les types

- Une condition sur un type brise de nombreuses règles (par exemple *Single Responsibility Principe*, *Open Closed Principle*). Le polymorphisme est toujours préféré : les conditions sur des types ne doivent être présentes que dans les classes de bas niveau, pour mettre en place le polymorphisme (par exemple dans le cas d'une Factory). (p.42 à 44)

### Choisir des noms descriptifs

- Une courte fonction qui ne fait qu'une chose est bien plus simple à nommer. (p.44)
- N'ayez pas peur de créer un long nom. Un long nom descriptif vaut mieux qu'un nom court énigmatique. (p.44)

### Arguments d'une fonction

- Idéalement, une fonction est *nilandique* (aucun argument). Les fonctions *monadiques/unaires* (un argument) ou *diadiques* (deux arguments) sont acceptables. Les fonctions *triadiques* (trois arguments) doivent être évitées autant que possible. Celles *polyadiques* (plus de trois arguments) ne doivent jamais être employées sans une excellente raison. À noter qu'un nombre variable d'arguments (`*args`) est équivalent à une liste s'ils sont traités de manière identique, et compte de ce fait comme un seul argument. (p.45)
- Avoir un nombre d'arguments très restreint permet de grandement simplifier les tests : moins d'arguments, c'est moins de combinaisons à tester. (p.45)
- Les arguments indicateurs sont une mauvaise pratique : cela complique la signature et annonce que la fonction fait plusieurs choses. E.g. `italic` dans `print(message: str, italic: bool)` est un argument indicateur et il convient de décomposer en deux fonctions : `print(str)` et `print_italic(str)`. (p.46)
- Il existe 3 types de fonctions, et une fonction ne peut être que d'un type : 
  - Une *demande* questionne sans rien changer et retourne une information. E.g. `file_exists(str) -> bool`.
  - Une *commande* manipule un élément pour retourner un élément. L'élément retourné est un nouvel élément, e.g. `open(str) -> InputStream`. En orienté objet, une commande peut s'appliquer sur un objet et n'aura pas besoin de retourner un élément, e.g. `user.add_one_year()`.
  - Un *évènement* modifie l'état du système. E.g. `print(str) -> None`.
(p.46)
- Les fonctions diadiques sont parfaites si les arguments sont des éléments ordonnés d'un même type, e.g. `point = Point(12, 3)`. Si ce n'est pas le cas, elles ne sont pas diaboliques, mais complexifient le code : e.g.   `write(a, b)` est moins clair que `a.write(b)` car l'ordre n'est pas naturel. (p.47)
- Si vous rencontrez des fonctions qui semblent avoir besoin de plus de deux arguments, essayez de les regrouper en une classe. En effet, cet ensemble d'argument est sans doute un concept qui mérite son propre nom. E.g. `make_circle(x, y, radius)` devient `make_circle(point, radius)` (p.48)

### Exceptions

- Il n'y a pas de raison d'utiliser des codes d'erreur dans les langages permettant les exceptions. (p.51)
- Si une fonction peut lever des exceptions, écrire les `try/except` dans une autre fonction qui appellera ladite fonction : en effet, une fonction ne fait qu'une seule chose. (p.52)

### Ne vous répétez pas

- Le code doit suivre le principe DRY (*Don't Reapeat Yourself*). Cela permet de garder le code compact et de pouvoir effectuer les modifications à un seul endroit. (p.54)

### Programmation structurée

- La programmation structurée n'est utile qu'avec des longues fonctions. En gardant les fonctions courtes, appliquer ce principe apportera plus de contraintes et de problèmes que d'avantages. (p.54 à 55)

## Chapitre 4 : Commentaires
> Ne commentez pas le mauvais code, récrivez-le.  
-- The Elements of Programming Style seconde édition, p.144, par Keprnighan et Plaugher, McGraw-Hill, 1978

- Rien n'est plus utile qu'un commentaire bien placé. (p.59)
- Rien ne peut encombrer un module autant que des commentaires dogmatiques sans importance. Ne jamais commenter des évidences. (p.59)
- Rien ne peut être plus préjudiciable qu'un ancien commentaire obsolète qui propage mensonges et désinformation. (p.59)
- Les commentaires sont, au mieux, un mal nécessaire. Ils pallient notre incapacité à exprimer nos intentions par le code. Lorsque vous exprimez le besoin d'écrire un commentaire, tentez d'abord d'améliorer votre code. En général, remplacer une opération complexe par un appel de fonction bien nommée ou une justification par une variable bien nommée dissipera le besoin de commenter. (p.60 à 61)
- Le code demeure la seule source d'informations absolument justes, les développeurs pouvant oublier de mettre à jour les commentaires. (p.61) 
- Les commentaires sont cependant utiles dans les cas suivants :
  - Expliquer les raisons un choix technique, e.g. "J'utilise un buble-sort plutôt qu'un fast-sort puisque [...]".
  - Clarifier des appels vers des fonctions peu claires que l'on ne peut pas modifier.
  - Avertir des conséquences possibles, e.g. "Attention, cette fonction est très lente, si vous acceptez une marge d'erreur de x% préférer la fonction func2".
  - Amplifier l'importance d'un point.
  - TODOs.
  - Commentaires légaux, e.g. copyright.
(p.62 à 66)
