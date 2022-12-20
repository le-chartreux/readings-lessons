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
