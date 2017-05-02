# Base de la programmation orienté objets

## Introduction

Dans ce chapitre, nous allons découvrir qu'est-ce qu'une classe et qu'est-ce qu'un objet, et nous allons apprendre à les utiliser dans un programme Javascript.

## Classes et objets

Si vous avez précédemment utilisé un language comme C++, vous serez peut-être familiés avec les structures.
Comme leur nom l'indique, ce sont des structures de données, un regroupement de variables de types différents, sous un nom
```c++
struct Humain
{
  string Nom;
  string Prenom;
  int age;
  bool aFaim;
};
```

Un objet est similaire à une classe, c'est un regroupement de données. Mais en plus de variables, un objet peu également contenir des fonctions.
Ces fonctions peuvent agir sur l'objet lui-même, et elles peuvent, comme toutes autres fonctions, prendre des paramètres et retourner des valeurs.

Je vais maintenant introduir le concept d'instance, qui est très important.
Un objet est l'instance d'une classe. Qu'est-ce que ça veut dire ?

Immaginez une usine de robots.
Dans l'usine, nous avons un ingénieur, et un constructeur.
L'ingénieur créé les plans d'un robot nommé *RobotBasique*. Il met sur papier tout ce qui fera partie du robot, mais sans jamais réellement créer celui-ci. Il créé l'équivalent de la **classe**.
Puis vient le constructeur. Il prend les plans de l'ingénieur et construit le robot, lui donnant au passage un nom unique : *PremierRobot*. Il vient de créer un **objet**, en se basant sur une **classe**.

Voici la définition d'une classe en javascript.

```javascript
class RobotBasique
{
  constructor(nombreDeBras)
  {
    this.bras = nombreDeBras;
  }
  
  afficheBras()
  {
    console.log(this.bras);
  }
}
```

Après avoir executé ce code, rien n'a été créé. On a informé notre script qu'un robot basique possède une variable définissant son nombre de bras ainsi qu'une fonction qui affiche dans la console cette variable.
Pour créer notre fameux *PremierRobot*, nous allons utiliser *RobotBasique* comme s'il s'agissait d'un type de variable et dire :

```javascript
RobotBasique PremierRobot = new RobotBasique(15);
PremierRobot.bras+=2;
PremierRobot.afficheBras();
```
Nous avons créé l'objet *PremierRobot*, qui est de type *RobotBasique*, et qui est égale à une nouvelle **instance** de *RobotBasique*, avec 15 bras.
Nous avons également accédé au nombre de bras afin d'en ajouter 2. Puis nous avons appelé la fonction qui permet d'afficher ce nombre automatiquement dans la console.

Voici donc le fameux concept d'instance. PremierRobot est une instance de RobotBasique. Et il pourrait y avoir autant de RobotBasique que vous le souhaitez, tous ayant un nom différent, et des valeurs différentes.


## Constructeur

Dans l'exemple précédant, j'ai parlé que l'usine employait un constructeur, chargé de prendre les plans (la classe) et de réaliser un robot avec.
En programmation, la fonction **constructor** est la fonction appelée lors de la création de l'objet.
On utilise cette fonction pour initializer l'objet, la plupart du temps.

.. to continue



