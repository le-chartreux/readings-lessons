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
- Le travail n'est pas terminé lorsque le code fonctionne. Il l'est après l'avoir également organisé et nettoyé. (p.151) 

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

## Chapitre 5 : Mise en forme

- La mise en forme est extrêmement importante : elle relève de la communication, et la communication est le premier commandement du développeur professionnel. (p.84)
- Les fichiers courts sont généralement plus faciles à comprendre que les fichiers longs. (p.85)
- Nous voulons qu'un fichier source ressemble à un article de journal :
  - Le nom doit être simple, mais explicatif. Il doit nous permettre de déterminer si nous examinons le bon module.
  - Les parties initiales doivent fournir des concepts de haut niveau et des algorithmes.
  - Le niveau de détails doit augmenter au fur et à mesure que nous descendons vers le bas du fichier source pour arriver à la fin où se trouvent les fonctions et les détails de plus bas niveau.
(p.86)
- Lorsque nous parcourons un fichier vers le bas, nos yeux sont attirés par la première ligne qui suit une ligne vide. De ce fait, les concepts (fonctions, méthodes, variables de classe, etc.) doivent être séparées par des lignes vides et le contenu des concepts doit être concentré. (p.86)
- Les concepts étroitement liés doivent être verticalement proches, du plus abstrait (en haut) au plus bas niveau (en bas). (p.88 à 89)
- Les variables doivent être déclarées au plus près de leur utilisation : il est inutile de commencer la fonction par toutes les déclarations. (p.89)
- Il faut déclarer les variables d'instance au tout début de la classe. (p.90)
- Si une fonction appelle une autre fonction, essayez de déclarer la fonction appelée directement après la fonction appelante : cela permet d'avoir un flux de lecture naturel de haut en bas. (p.91)
- Il est préférable de déclarer une constante à l'endroit où elle a un sens, puis de la passer en paramètre vers les fonctions de plus bas niveau plutôt que de la mettre dans les fonctions de bas niveau, e.g. 
```python
def make_response(request: Request) -> Response:
    page_name = get_page_name_or_default(request, "front page")  # "front page" est la constante
  ...

def get_page_name_or_default(request: Request, default_page_name: str) -> str:
  # ça n'aurait pas de sens d'enfouir la valeur par défaut ici
  page_name = request.get_page_name()
  return default_page_name if page_name.is_blank() else page_name
```
- Il est préférable de garder des lignes de moins de 80 caractères. Les lignes de plus de 120 caractères doivent être évitées. (p.94)
- Les espacements horizontaux doivent refléter la liaison étroite entre les éléments :
  - Il existe une liaison étroite entre une fonction et ses parenthèses ainsi que les opérateurs unaires : ils ne doivent donc pas être séparés. E.g. `func_a()`, `a++`, `-a`
  - Les opérateurs binaires (`=`, `+`, `,`, etc.) doivent être espacés pour les accentuer, e.g. `a = b + 3`,  `a = [1, 2, 4]`. Il est cependant possible de ne pas séparer ceux qui ont une priorité plus élevée pour faciliter la lecture de longues équations, e.g. `a = 1 + 2*x + x**3` (p.94 à 95) 
- Ne pas tenter d'aligner les noms, types et assignations. Cela diminue la lisibilité en insistant à lire cela comme les colonnes d'un tableau et non pas une succession de lignes. Si vous ressentez le besoin d'aligner une longue liste de déclarations, **le problème est la longueur de la liste**, non pas l'absence d'alignement. C'est un indicateur que votre classe est trop grande et devrait être divisée. Par aligner, on entend ceci : 
```python
first_name:    str           = "default_first_name"
last_name:     str           = "default_last_name"
birth_date:    datetime.date = datetime.date.fromisocalendar(1900, 01, 01)
city_of_birth: str           = "default_city"
...
```
- L'indentation est essentielle dans la compréhension d'un code. Elle est obligatoire en Python, nous n'avons de ce fait pas ce problème. (p.98)
- L'équipe doit suivre les mêmes règles pour avoir un style cohérent et fluide. Ne pas l'appliquer compliquera inutilement le code source. (p.99)

## Chapitre 6 : Objets et structures de données

- Nous voulons que les variables soient privées pour que personne d'autre n'en dépende, ce qui nous permet de les modifier librement. Il est stupide de créer des accesseurs pour exposer les variables comme si elles étaient publiques si ce n'est pas nécessaire. Il faut uniquement exposer les opérations. E.g. si pour un véhicule on veut connaitre son pourcentage de carburant restant, fournir `get_percent_fuel_remaining()` et non pas `get_fuel_tank_capacity()` et `get_gallons_of_gasoline()`(p.103 à 105)
- Au contraire, pour stocker uniquement des données, créer des structures (`dataclass` en Python). Elles ne doivent pas avoir de méthodes et tous leurs attributs sont publics. (p.105)
- Nous devons rester le plus abstrait possible dans les classes, e.g. si nous avons une voiture et que la seule information qui nous intéresse est à sa capacité à transporter des choses, il ne faut pas créer une classe `Car` mais une classe `Transporter`. (p.104 à 105)  
- Un code procédural (= qui utilise des structures de données) facilite l'ajout de nouvelles fonctions sans modifier les structures de données existantes. Un code orienté objet facilite l'ajout de nouvelles classes sans modifier les fonctions existantes. (p.107)
- Loi de Déméter : une méthode `f` d'une classe `C` ne doit appeler que les méthodes des éléments suivants : 
  - `C`.
  - Les objets créés par `f`.
  - Les objets passés en argument à `f`.
  - Les objets contenus dans des variables d'instance de `C`.
Le non-respect de la loi de Déméter indique souvent que la fonctionnalité que nous souhaitons implémenter n'est pas au bon endroit : elle devrait être dans les objets avec lesquels nous interagissons. Dans le cas où il s'agit uniquement de lectures de valeurs, c'est un problème qui peut être tolérable. Les écritures sont intolérables.
E.g. le code suivant ne suit pas la loi de Déméter :
```python
def add_5_people_to_hometown_population(self: User) -> None:
    city = self.address.get_city()  # appel d'une méthode d'un objet d'instance -> OK
    population = city.get_population()  # ne rentre dans aucun des cas autorisés & lecture -> pas OK
    city.set_population(population + 5)  # ne rentre dans aucun des cas autorisés & écriture -> intolérable
```
(p.108 à 110)

## Chapitre 7 : Traitement des erreurs

- Utiliser des exceptions et non des codes de retour. (p.114)
- Une exception lancée qui n'a pas vocation à arrêter complètement le système devrait être capturée le plus tôt possible, idéalement dans sa fonction, ou dans la fonction appelante. La traiter plus loin est une violation de l'OCP (*Open/Closed Principle*), car les fonctions doivent se soucier de détails d'implémentations de fonctions appelées par la fonction appelante. (p.117)
- Fournissez un contexte avec les exceptions, e.g. `FileNotFoundError(f"Le fichier res/config.json n'est pas disponible")`
- Ne pas retourner `null` (en Python None) mais une exception (ou une liste vide). Cela limitera grandement les risques de `NullPointerException`. (p.121 à 122)
- Ne pas passer `null` à des fonctions. Cela ne peut poser que des problèmes. (p.123)
- Traiter séparément la gestion des erreurs et la logique principale. (p.123)

## Chapitre 8 : Limites

- Essayez de garder locaux (ni les passer à des fonctions ni les retourner) les objets modifiables librement si vous comptez les réutiliser, e.g. :
```python
def do_something(self: User) -> list[Project]:
    result = do_something(self.projects)  # non : la fonction appelée pourra modifier projects librement
    return self.projects  # non : la fonction appelante pourra modifier projects librement
```
(p.126-128)
- En utilisant une API tierce, effectuez des *tests d'apprentissage* : écrivez des tests sur les fonctionnalités de cette API que vous comptez utiliser. Cela vous permettra d'apprendre l'API et de vous assurer qu'elle fonctionne. Cela simplifiera également énormément la migration : vous pourrez tester l'installation d'une nouvelle version très efficacement. (p.128)
- Plus qu'ailleurs, limiter au maximum les endroits qui interagissent avec le code tiers. Si besoin, utiliser un adaptateur (design pattern). (p.132)

## Chapitre 9 : Tests unitaires

- Les tests unitaires bien écrits participent à l'expressivité en servant de documentation par l'exemple. (p.188) 
- pas lu

## Chapitre 10 : Classes

- Les constantes statiques publiques viennent en premier, puis les variables statiques privées et les variables d'instance privées. (p.148)
- Suivre la règle de décroissance dans l'organisation des fonctions. (p.148)
- Le `protected` est tolérable, mais à éviter. (p.148)
- Une classe doit avoir une seule *responsabilité* (*Single Responsibility Principle*). S'il existe plusieurs raisons qui pourraient amener à modifier la classe, elle ne respecte pas ce principe. (p.150)
- Le nom d'une classe doit refléter sa responsabilité : si vous n'arrivez pas à lui trouver un nom concis sans être ambiguë, elle est sans doute trop grande. (p.150)
- Il doit être possible de décrire la classe en moins de 25 mots, sans *si*, *et*, *ou*, *mais*. Si ce n'est pas le cas, elle a trop de responsabilités. (p.150)
- Un code contenant beaucoup de classes à usage unique n'est pas plus long ni compliqué à comprendre qu'un code avec quelques classes à usage multiple. La question est de savoir si vous voulez que vos outils soient rangés dans une boite à outils avec de nombreux petits tiroirs contenant des éléments parfaitement définis et étiquetés, ou si vous voulez avoir quelques tiroirs dans lesquels vous mettez tous vos outils en vrac. La seconde solution oblige à patauger parmi un grand nombre de choses dont vous n'avez pas forcément besoin sur le moment. (p.152)
- Nous voulons une cohésion élevée entre les méthodes et leur classe. Plus une méthode utilise de variables d'instance, plus la cohésion est forte. Cela signifie que les méthodes et les variables de la classe sont indépendantes et forment un tout logique. (p. 152) 
- Si vous commencez à avoir un grand nombre de variables d'instance utilisées par un sous-ensemble de méthodes, essayez de découper la classe. Le découpage de longues fonctions nous donne souvent une classe avec beaucoup de variables d'instance, qui doit être découpé en plusieurs classes mieux organisées, plus transparentes et plus cohérentes. (p.153)
- Les programmes qui utilisent le principe de responsabilité unique sont plus longs que ceux fourre-tout, mais sont documentés par le code explicite. (p.158)
- Respecter le DIP (*Dependency Inversion Principle*) : les classes ne doivent dépendre que d'abstractions (donc de classes abstraites), pas de détails concrets. Cela facilitera énormément le test : il suffira de donner une classe de test implémentant l'abstraction. (p.163)

## Chapitre 11 : Systèmes

- Les villes fonctionnent car elles disposent d'équipes de plusieurs personnes qui prennent en charge chaque aspect (eau, électricité, trafic, respect de la loi, etc.). Certaines personnes sont responsables de la vue d'ensemble, tandis que d'autres se focalisent sur les détails. (p.166)
- Séparer la construction du système (son initialisation/démarrage) de son utilisation. Une manière simple de le faire est de déplacer tous les aspects de construction dans le `main` (ou dans des modules appelés par `main`), puis concevoir le reste du programme en supposant que tout soit correctement construit et lié. À l'exécution, la fonction `main` initialise les objets nécessaires au système (cela peut être également des factory), puis les passe à l'application. (p.167) 
- Il est impossible que le système soit parfait dès le départ. Il est amené à grandir, et les tests et le code propre sont à ce moment extrêmement utiles. (p.170)
- Les différents domaines d'une architecture de système doivent être incorporés à l'aide d'aspects minimalement invasifs ou d'outils de type aspect. (p.180)
- Il faut reporter des décisions jusqu'au dernier moment possible, pour avoir le plus d'informations à notre disposition. (p.181)
- Que vous conceviez des systèmes ou des modules individuels, n'oubliez jamais d'utiliser les choses les plus simples qui fonctionnent : KISS (*Keep It Short and Simple*). (p.182)

## Chapitre 12 : Émergences

- Les quatre règles de conception simple selon Kent Beck, par ordre d'importance :
  - Elle réussit tous les tests. Un système non vérifiable ne doit jamais être déployé. L'écriture de tests conduit à une meilleure conception.
  - Elle ne contient aucune redondance
  - Elle exprime les intentions du programmeur
  - Elle réduit le nombre de classes et de méthodes
  - Il est facile d'écrire du code que *nous* comprenons, car, au moment où nous l'écrivons, nous sommes au cœur du problème. Les autres personnes chargées de la maintenance du code n'en auront pas une compréhension aussi profonde. (p.188)
