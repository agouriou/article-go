package
private/public -> majuscules
plusieurs return
try, catch --> err
pointeurs!
pas de code inutilisé (_ pour les variables)


2e article
chan, subroutines


# Un aperçu du langage Go pour les développeurs Java

On entend de plus en plus parler du langage Go, notamment parce que c'est le langage utilisé pour Docker et une bonne partie de l'écosystème Docker.
Mais alors concrètement, Go ça ressemble à quoi? Cet article a pour but de vous introduire à la syntaxe de Go et à quelques éléments qui pourraient vous 
paraître bizarre, notamment si vous venez du monde Java.
Bien que le point de vu adopté soit celui d'un développeur Java, tout développeur souhaitant une introduction à Go pourra y trouver des éléments intéressants.

## Go c'est quoi?
Go est un langage compilé, fortement typé, proposant des concepts pour faciliter la programmation concurrente. 
Son objectif est d'être (presque) aussi performant que du C, tout en proposant une écriture simplifiée. Ainsi, la gestion de la mémoire est simplifiée par rapport à du C.
Comme dans Java, un garbage-collector est utilisé. L'algorithme de garbage collection utilisé a fréquemment évolué au cours des versions du langage. 


## Déclaration de variable et inférence de type

En Go, la déclaration de variable est inversée par rapport au Java. Le nom est en première position et est suivi du type `var i int = 3`. 
L'opérateur `:=` est un raccourci permettant de déclarer et d'initialiser une variable dont le type est inféré.

## Packages & visibilité
Une application Go est organisée en différents packages. Le point d'entrée d'une application est la fonction "main", dans le package "main".
Comme en java, il est possible d'importer un package pour en utiliser les objets/fonctions. En revanche ici, il n'y a pas de mot clef "private, protected, public". 
Pour rendre une fonction visible à l'extérieur du package, il faut mettre sa première lettre en majuscule. Un peu perturbant quand on est habitué au *lowerCamelCase*!

```
package foo

func visibleSeulementDansLePackage(){...}

func VisibleAussiEnDehorsDuPackage(){...}
```

## Return multiples 
En tant que développeur Java, une chose surprenante est la possibilité de renvoyer plusieurs valeurs. Dans l'exemple ci-dessous, la fonction renvoit une string et un int. 

```
func foo()(string, int){
  someString = "aaa"
  i = 3
  return someString, i
}
```

On peut nommer les éléments renvoyés afin de les référencer dans le corps de la fonction. Il devient alors optionnel de spécifier les variables à la suite du return.

```
func foo()(str string, i int){
  str = "aaa"
  i = 3
  return 
}
```

Attention à ne pas abuser de cette possibilité. En Java il arrive de tomber sur des méthodes prenant en entrée 6 ou 7 paramètres, imaginez en plus qu'il y ait 7 objets renvoyés...


## Gestion des erreurs
Il n'y a pas d'exception en Go, pas de `try-catch` ni de `throws`! A la place, on utilise intensivement le mécanisme de retour multiple. Il est commun d'avoir 2 éléments retournés par une fonction: le premier élément est le retour normal, 
le second élément est une éventuelle erreur.

```
file, err := os.Create("superfichier.txt")
if err != nil {
	log.Fatal(err)
}
```

Le code devient donc rapidemment plein de `if` vérifiant les cas d'erreurs. 

## Pointeurs


## Interface et implémentation implicite


## Programmation conccurente

