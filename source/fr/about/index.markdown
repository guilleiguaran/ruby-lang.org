---
layout: page
title: "À propos de Ruby"
date: 2011-08-05 22:08
comments: false
sharing: false
footer: false
---
Indéniablement, Ruby devient de plus en plus populaire. Les « rubyistes
» qualifient ce langage d’élégant, voire lui prêtent des qualités
artistiques ; ils soulignent dans le même temps qu’il est pratique à
utiliser et facile d’accès. Mais tout ça est très éthéré, qu’en est-il
concrètement parlant ?

### Ruby, une conceptualisation personnelle

Le langage ruby, en terme de syntaxe et de fonctionnalité, a été dès le
départ conçu comme un ensemble homogène. Son créateur est le programmeur
japonais [Yukihiro « matz » Matsumoto][matz]. Ce dernier a rassemblé certaines fonctionnalités de ses
langages préférés de l’époque (principalement Perl, Smalltalk, Eiffel,
Ada et Lisp) afin d’imaginer un nouveau langage qui mêlerait
astucieusement programmations impérative et fonctionnelle. À plusieurs
reprises, il a déclaré que son but était « d’essayer de rendre Ruby le
plus naturel possible, pas nécessairement simple. »

À ce propos, il a ajouté :

{% blockquote liste de diffusion Ruby-Talk http://blade.nagaokaut.ac.jp/cgi-bin/scat.rb/ruby/ruby-talk/2773 12 mai 2000 %}
Ruby est simple en apparence, mais son architecture interne est très complexe — tout comme notre corps peut l’être.
{% endblockquote %}

C’est cette approche qui a été maintenue depuis lors, pour faire de Ruby
un langage robuste, porté par une syntaxe naturelle.

### La croissance de Ruby

Depuis sa publication en 1995, Ruby a progressivement intéressé de plus
en plus de programmeurs venant des quatre coins du monde. En 2006, Ruby
rassemblait une masse critique d’utilisateur et gagnait une réelle
reconnaissance. Aujourd’hui, des groupes d’utilisateurs existent dans
les plus grandes villes du monde, et les (nombreuses) conférences à
propos de Ruby affichent complet.

Ruby-Talk, la toute première [liste de diffusion][listes de diffusion] recevant les
discussions à propos du langage Ruby, atteint aujourd’hui une moyenne de
deux cent nouveaux messages par jour.

L’index TIOBE, qui mesure la croissance des langages informatiques,
place Ruby à la dixieme place du classement des langages les plus
utilisés au monde. Concernant cette évolution, leur prédiction est la
suivante : « il y a des chances que Ruby entre dans le top 10 dans moins
de six mois. » La plus grande part de cette accélération semble revenir
à la popularité de certains logiciels écrits en Ruby, notamment le
framework web [Ruby on Rails][RoR].

Par ailleurs, Ruby est [totalement libre][license]. Il est non seulement
gratuit, mais son utilisation, sa copie, sa modification et sa
distribution sont également libres.
### Une complète orientation objet

Initialement, Matz a étudié les autres langages afin de définir une
syntaxe qui lui serait idéale. Se remémorant cet épisode, il nous
rapportait : « je voulais un langage de script plus puissant que Perl,
et plus orienté objet que Python([1][])".

Dans Ruby, le paradigme de base est que tout y est un objet. Chaque
entité d’information et de code peut recevoir ses propres propriétés et
actions. La programmation orientée objet fait référence aux propriétés
sous le terme de *variables d’instance*, et aux actions sous le nom de
*méthodes*. L’approche purement objet de Ruby est très souvent illustrée
par un bout de code montrant l’application d’une action à un nombre.

``` ruby
    5.times { print "Nous **adorons** Ruby — un peu trop peut-être !" }
```

Dans beaucoup de langages, les nombres et autres types primaires ne sont
pas des objets. Ruby suit ici la voie de Smalltalk, en donnant accès aux
méthodes et variables d’instance à tous les types. Cela facilite
l’appropriation de Ruby, puisque les règles s’appliquant aux objets
usuels s’appliquent en fait à travers tout Ruby. Par ailleurs, la
syntaxe est triviale, se rapprochant d’une phrase minimaliste en
anglais.

### Un soucis de flexibilité

Ruby a pour réputation d’être un langage très flexible, autorisant
notamment son utilisateur à en modifier les entrailles durant
l’exécution. Des parties importantes de Ruby peuvent être retirées ou
redéfinies à loisir ; des greffes de fonctionnalités sont possibles en
cours de route. En définitive, Ruby essaye de ne pas contraindre le
programmeur, mais de lui fournir un squelette robuste autour duquel
bâtir des applications.

Par exemple, l’opération arithmétique d’addition est réalisée par
l’opérateur plus (`+`). Mais si vous préférez utiliser une méthode
`plus`, vous pouvez l’ajouter à la classe de base `Numeric` de Ruby :

``` ruby
    class Numeric
      def plus (x)
        self.+(x)
      end
    end

    y = 5.plus 6
    # y vaut maintenant 11
```

Tous les opérateurs de Ruby sont des méthodes pensées pour être aussi
pratique que faire se peut, syntaxiquement parlant. Vous pouvez
toutefois les redéfinir à votre convenance.

### Les blocs, un moyen d’expression à part entière

L’usage que fait Ruby des blocs de code est également reconnu comme
étant une grande source de flexibilité. Un programmeur peut associer à
toute méthode une *closure*, un bloc de code « anonyme » décrivant la
manière dont la méthode doit se comporter. Une telle *closure* est
appelée en Ruby un *bloc*. Cette fonctionnalité est rapidement devenu
l’une des plus populaires auprès des nouveaux utilisateurs de Ruby,
habitués à des langages impératifs comme PHP ou Visual Basic.

Les blocs trouvent leur inspiration dans les langages fonctionnels. Matz
a dit à ce propos : « en créant les *closures* de Ruby, je souhaitais
respecter la voie tracée par Lisp([4][]). »

``` ruby
    search_engines = %w[Google Yahoo MSN].map do |engine|
      "http://www." + engine.downcase + ".com"
    end
```

Dans le code ci-dessus, le bloc est délimité par la structure
`do ... end`. La méthode `map` applique le bloc à la liste de mots
fournie en premier lieu par un simple tableau. Bien d’autres méthodes en
Ruby laissent au programmeur l’opportunité d’écrire leurs propres blocs,
afin de d’adapter le fonctionnement d’une méthode au contexte du script.

### Le mécanisme de *mixin*

À la différence de bien d’autres langages orientés objet, Ruby ne donne
accès qu’à l’héritage unique, et ce, **volontairement**. En effet, Ruby
supporte par ailleurs le concept de modules (similaires au *Categories*
en Objective-C). Ces modules sont des regroupements de méthodes.

Les classes peuvent « incorporer » un module (opération dite de *mixin*)
afin d’en recevoir toutes les méthodes, sans plus de travail. Par
exemple, toute classe implémentant une méthode `each` peut ensuite
incorporer le module `Enumerable`, lequel fournit gratuitement plusieurs
méthodes utilisant `each` pour faire des boucles.

``` ruby
    class MonTableau
      include Enumerable
    end
```

En général, les rubyistes préfèrent cette façon de faire à l’héritage
multiple, qui est complexe et peut se révéler trop restrictif.

### Le fond et la forme

Bien que Ruby fasse un usage très limité de la ponctuation et se
concentre sur des mots clé simples en anglais, quelques signes de
ponctuation agrémentent la syntaxe. Ruby ne requière pas la déclaration
des variables. Plus simplement, une convention de nommage est utilisée
pour indiquer la portée des variables.

- `var` pourrait être une variable locale.
- `@var` est une variable d’instance.
- `$var` est une variable globale.

Ces signes améliorent la lisibilité en permettant une identification
rapide du rôle de chaque variable. Il devient ainsi inutile de préfixer
chaque variable d’instance d’un `self.` redondant.

### Au delà de ces bases

Ruby met à disposition du programmeur bien d’autres fonctionnalités,
parmi lesquelles on peut citer…

-   une gestion des exceptions, tout comme Java ou Python, afin de gérer
    facilement les erreurs ;
-   un ramasse-miettes (*garbage collector*) utilisant l’algorithme
    *mark-and-sweep* pour gérer tous les objets. Il n’y a pas non plus
    besoin de maintenir un compte des références individuelles dans les
    bibliothèques d’extensions en C. Comme Matz le dit si bien, « c’est
    un bon point pour votre santé » ;
-   la possibilité d’écrire des extensions en C est plus simple qu’en
    Perl ou Python, grâce à une API élégante permettant d’appeler Ruby
    depuis le C. Cela comprend aussi bien les appels à Ruby au sein d’un
    logiciel, que l’utilisation de Ruby comme langage de script. Une
    interface SWIG est également disponible ;
-   la possibilité de charger une bibliothèque d’extension à la volée,
    si le système d’exploitation le permet ;
-   une très grande portabilité : développé majoritairement sous
    GNU/Linux, Ruby fonctionne aussi sur une grande part des UNIX, Mac
    OS X, Windows 95/98/Me/NT/2000/XP, DOS, BeOS, OS/2, etc.
