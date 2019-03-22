Fait par Martin Chauvin et Théo Ponton le 22/03/2018

# Implémentations d'images hybrides

Le but de notre travail est de réaliser des images hybrides. C'est à dire qu'à l'aide d'une image1 (par exemple un chat) et d'une image2 (par exemple un chien), il s'agit de créer une image composée des 2 appelée image hybride. Elle est de telle sorte que lorsqu'on la regarde de près, on voit l'image1 (le chat ici) et lorsqu'on la regarde de loin, on voit l'image2 (le chien). 

![test](..\code\img\chat.jpg)![test](..\code\img\chien.jpg)![result_N5.png](../code/results/result_N5.png)

## Algorithme global

L'idée pour réaliser ces images, c'est d'appliquer un filtre passe-bas sur le chat et un filtre passe-haut sur le chien. Ainsi, de près on verra plus les basses fréquences et de loin les hautes fréquences. 

L'algorithme est le suivant :

- **Descente de la pyramide gaussienne** : sur l'une des images, nous allons appliquer un filtre gaussien d'une taille 7x7 qui va flouter l'image puis nous allons réduire la taille de l'image par 2. Sur la nouvelle image obtenue, nous repasser le même filtre gaussien puis à nouveau diviser la taille de l'image par deux. Le flou de l'image va permettre d'avoir une image moyennée et donc des basses fréquences.
- **Descente de la pyramide laplacienne** : sur la seconde image, nous allons lui soustraire un filtre gaussien appliqué à elle-même puis diviser la taille par 2. Sur l'image obtenue, nous allons à nouveau lui soustraire le filtre gaussien appliqué à cette dernière et ainsi de suite. Cette opération revient à enlever la moyenne à l'image. En enlevant la moyenne à une image, il reste juste les détails qui sont en réalité les hautes fréquences. 
- **Remontée de la pyramide** : 