# Projet P5
Dans ce chapitre, nous allons voir la constitution d'un projet P5.

## Fichiers
Pour commencer, nous allons répurérer la librairie P5 sur le site officiel.
Voici un [lien direct](https://github.com/processing/p5.js/releases/download/0.5.8/p5.min.js "Librairie P5") vers la version complete et compressée.

Enregistrez ce fichier à la racine de votre projet Git, créé durant [l'introduction](1-Introduction.md "Introduction du tutoriel").
Nous allons maintenant créer une page HTML, car après tout, Javascript n'est rien sans page web.
Ouvrez le dossier du projet dans Visual Studio code (clique droit sur le dossier, *Open with Code*).
Créez un nouveau fichier dans le dossier et nommez-le `index.html`.
Dans ce fichier, collez le code suivant :
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="utf-8">

    <script src="p5.min.js"></script>
    <script src="sketch.js"></script>

</head>
<body>
</body>
</html>
```
C'est le minimum vital pour faire une page web, plus deux lignes spéciales sur lesquels nous allons nous attarder :
`<script src="p5.min.js"></script>` permet d'inclure la librairie que nous avons téléchargée.
`<script src="sketch.js"></script>` permet de la même manière, d'inclure un fichier *sketch.js*, qui n'existe pas encore.

Nous allons le créer dès à présent, de la même manière que pour le fichier html.
> Astuce : vous pouvez également faire *ctrl+clic* sur le nom du fichier dans la balise html, vs code vous dira qwe le fichier n'existe pas et vous proposera de le créer.

## Structure P5
Nous avons créé un fichier nommé *sketch.js*. Annalysons tout d'abord le nom de ce fichier.
*sketch* est le nom "par défaut" pour les fichiers P5. Vous pouvez mettre n'importe quoi, mais c'est le nom standard, que nous allons conserver pour des raisons pratiques.
*.js* est l'extension du fichier, il s'agit d'un fichier standard Javascript.
Comme nous avons également inclu la librairie, nous aurons accès dans ce fichier aux fonctions de P5.

Le principe de P5 est le suivant :
- Une fonction de mise en place
- Une fonction d'affichage

```javascript
function setup()
{
}

function draw()
{
}
```

La fonction de mise en place *setup* est executée une fois au début du programme, puis la fonction d'affichage *draw* est executée en boucle un certain nombre de fois par seconde (suivant les FPS).

Analysons plus en détail notre premier élément javascript : la fonction.
Le **mot clé** `function` nous permet de dire à javascript que ce qui suit sera une fonction.
S'en suit le **nom** de la fonction, qui peut être n'importe quoi `setup`.
Puis des parenthèses s'ouvrent et se referment `()`. Dans l'exemple ci-dessus, elles sont vides, mais c'est dans celles-ci que nous pourrons passer des **paramètres**, dans un futur turoriel.
Finalement, on ouvre un **bloc d'instruction** avec des accolades. `{}`

Contrairement à certains languages comme C++ ou Java, le Javascript se moque de quel type de donnée notre fonction va retourner.
C'est pareil pour  les variables qui, comme par exemple en Python, ne sont pas typées (n'ont pas de type).

Maintenant que nous savons ce qui se passe, nous allons créer un **canvas**.
Un canvas est un élément HTML dans lequel on peut dessiner.
P5 propose des fonctions pour en créer un facilement puis y dessiner.

Je vais parler de différentes fonctions de la librairie, mais je ne pourrai pas toutes les couvrir. Un bon endroit pour en apprendre plus de votre côté est la [documentation P5](http://p5js.org/reference/), qui contient beaucoup d'exemple pour toutes les fonctionnalitées de la librairie.

Justement, rendons-nous sur la documentation pour la fonction `createCanvas`.
Cliquez sur le lien ci-dessus et cherchez avec *ctrl+F* dans la page le nom de la fonction.
On peut voir que cette fonction créé un canvas de la largeur et hauteur donnée en pixel.

Ecrivez la fonction setup vue ci-dessus et à l'intérieur du bloc d'instruction, appelez la fonction comme ci-dessous.

```javascript
function setup()
{
    createCanvas(800,600);
}
```

Quelques nouveautées sont apparues. Nous avons appelé une fonction définie non pas dans notre fichier mais dans la librairie en écrivant son nom et en entrant des valeurs pour ses paramètres. Notez que les lignes finissent par un point virgule `;`.
Ces points virgule n'est pas obligatoires pour que le code soit executé, mais il est de bonne pratique de les utiliser.

Nous allons appeler une seconde fonction pour remplir notre canvas avec une couleur unie.
Cette fonction est nommée `background`. Vous pouvez allez la chercher sur la documentation, et vous trouverez qu'elle demande une couleur en paramètre.

Les couleurs dans P5 peuvent être représentées de pleins de manières différentes.
Si vous passez un seule valeur à `background` entre 0 et 255, il va l'interpréter comme une valeur de gris. Vous pouvez également passer trois valeurs entre 0 et 255 séparées par des virgules et elles seront interprétées en tant que *rouge*, *vert* et *bleu*.

Nous allons remplir le fond en noir, nous pouvons donc utiliser une seule valeur, *0*.

```javascript
function setup()
{
    createCanvas(800,600);
    background(0);
}
```

Vous pouvez enregister le fichier javascript et vous rendre sur votre navigateur web.
Dans l'introduction, nous avons installé un serveur web, et nos fichiers se trouvent déjà au bon endroit pour être accessibles depuis le navigateur. Vérifiez que votre serveur web soit lancé et rendez-vous sur l'adresse `localhost`.
Une sorte d'explorateur de fichier devrait apparaître. CLiquez sur le dossier contenant vos projets, puis sur le dossier de ce projet.
Notre fichier html étant nommé *index.html*, le serveur web nous le donne directement lorsque nous entrons dans ce dossier.

Sur la page web, vous devriez voir une zone de 800x600 pixels noirs sur fond blanc. Félicitations !
Nous allons maintenant dessiner des *choses* sur cette page.

Et si nous codions un carré se dirigeant sur la droite de l'écran, puis rentrant sur l'écran de l'autre côté une fois hors de vue ?

Pour cela, nous allons avoir besoin de la fonction *draw*

en dessous de la fonction setup, hors de son bloc d'instruction

--to continue
