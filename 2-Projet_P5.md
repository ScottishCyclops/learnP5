# Projet P5
Dans ce chapitre, nous allons voir la constitution d'un projet P5.

## Fichiers de base
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
- `<script src="p5.min.js"></script>` permet d'inclure la librairie que nous avons téléchargée.
- `<script src="sketch.js"></script>` permet de la même manière, d'inclure un fichier *sketch.js*, qui n'existe pas encore.

Nous allons le créer dès à présent, de la même manière que pour le fichier html.
> Astuce : vous pouvez également faire *ctrl+clic* sur le nom du fichier dans la balise html, vs code vous dira qwe le fichier n'existe pas et vous proposera de le créer.

## Premier code
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

### Documentation P5
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

### Couleurs
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

### Dessinons un carré
Et si nous codions un carré se dirigeant sur la droite de l'écran, puis rentrant sur l'écran de l'autre côté une fois hors de vue ?

Pour cela, nous allons avoir besoin de la fonction *draw*

En dessous de la fonction setup, hors de son bloc d'instruction, nous allons écrire la fameuse fonction *draw*.

```javascript
function draw()
{
}
```

Nous la remplirons plus tard.
Tout d'abord, nous allons utiliser une autre fonction de P5 pour dessiner un carré. Cette fonction se nomme `rect`, raccourcis pour *rectangle*.
Si vous regardez la page de documentation de cette fonction, vous verrez que cete fonction nous demande une position *x* et *y*, un largeur et un hauteur.

La position *x/y* n'est autre que l'emlacement sur le canvas, exprimé en pixels. la postion *x* est la position horizontal, de 0 au nombre de pixels de large de notre canvas. Et *y* la position vertical.

En P5, l'origine (position 0,0) est en haut à gauche de du canvas. Les valeurs s'incrémentes en allant à droite et vers le bas.

Vous aurez compris qu'il nous faudra connaître plusieurs choses : la **taille du canvas**, la **position du rectange**, la **taille du rectangle**.
Il faudra donc stocker des valeurs. Ceci va nous introduire aux variables en javascript.

### Variables
```javascript
let a = 42;
let b = 'texte'
const c = true;
```
Le code ci-dessus créé plusieurs variables en javascript.
Le mot-clé `let` permet de dire que ce qui suit est une variable. Le mot-clé `const` permet de définir une constante, qui ne pourra pas être modifiée.
S'en suit le nom de la variable `a`. Puis un signe égal `=` pour affecter une valeur à cette variable.
Comme dit précédement, les variables js ne sont pas typées, on peut donc donner n'importe quel type de valeur, comme un nombre `0`, une chaine `'texte'` ou un booléen `true` (que nous revérons plus tard).

De retour à notre programme, nous allons nous déplacer tout en haut, au-dessus de la fonction setup.
Nous allons décalrer des constantes pour la largeur et hauteur de notre canvas.

```javascript
const LARGEUR = 800;
const HAUTEUR = 600;
```

Vous êtes libres d'utiliser la convention de nommage que vous souhaitez, mais restez consistant.

Pendant que nous commes là, nous allons déclarer quelques autress variables. Tout ce qui est déclaré ici, en dehors des fonctions, est global. Ces variables seront donc accessibles depuis partout dans notre programme, ce qui est exactement ce que l'on veut.

```javascript
//constantes
const LARGEUR = 800;
const HAUTEUR = 600;

//variables globales
let x;
let y;
let taille;
```

J'ai pour bonne habitude de ne pas initialiser des variables globales à leur création, sauf les constantes.
Vous remarquerez également que j'ai ajouté deux lignes qui commencent par des double slash `//`. Ce sont des commentaires uniligne.
Ce qui signifique que le reste de la ligne sera ignoré par le programme, mais certainement pas par nous.

Il n'est pas nécéssaire de commenter chaque ligne de code, mais un commentaire au-dessus d'une action louche est toujours utile pour vous plus tard, ou une autre personne voulant comprendre votre code.

Nous allons maintenant nous rendre dans la fonction setup pour affecter des valeurs de base à ces variables.

```javascript
//constantes
const LARGEUR = 800;
const HAUTEUR = 600;

//variables globales
let x;
let y;
let taille;
let couleurFond;

function setup()
{
    couleurFond = 0;
    
    createCanvas(LARGEUR,HAUTEUR);
    background(couleurFond);
    
    x = LARGEUR / 2;
    y = HAUTEUR / 2;
    taille = 10;
}
```

Beaucoup de choses se sont passées. J'ai ajouté une variable pour stocker la couleur du fond. Je dois affecter une valeur à celle-ci avant de l'utiliser.
J'ai utilisé mes constantes pour définir la taille du canvas.
Les autres variables sont définies à la fin de la fonction setup.
J'ai affecté comme position x et y par défaut le centre de l'écran grâce aux mathématiques.

### Math et nombres à virgules

```javascript
x = LARGEUR/2;
```

J'affecte à la variable x le résultat du calcule `LARGEUR / 2`. Largeur vaut `800`, en le divisant par deux, cela donne `400`, qui sera le centre de notre écran en largeur. Pareil pour la variable y.

Javascript s'occupe de décider si oui ou non il faut stoker un résultat à virgule ou pas. Mais dans ce cas, nous voulons éviter d'avoir un résultat non entier. Nous pouvons forcer le résultat sous forme d'entier grâce à la fonction `int()`

```javascript
x = int(LARGEUR/2);
```
Nous effecuons notre divison, puis la convertissons en entier et l'affectons à `x`.

### Dessiner
De retour dans notre fonction *draw*, que nous avions lâchement abandonnée, nous allons créer notre fameux carré avec la fonction rect. Un carré n'est autre qu'un rectangle de même largeur et hauteur !

```javascript
function draw()
{
    rect(x,y,taille,taille);
}
```

Nous avons maintenant dessiné un rectangle à la position *x/y* de taille *taille*.
Vous pouvez retourner sur la page web et la rafraichir et et et... Rien.
Nous n'avons pas dit à P5 de quel couleur dessiner le rectangle, il l'a donc dessiné en noir.

Ici, P5 nous montre ses spécificités. Au lieu de passer la couleur en paramètre du rectangle, nous allons définir la couleur de manière plus global avec la fonction `fill`.
Cette fonction, comme `background`, prend une couleur en paramètre, et va l'utiliser pour dessiner tout ce qu'on lui demande ensuite jusqu'à la prochaine instruction `fill`.
Nous voulons dessiner notre rectangle en rouge stylé, nous allons donc utiliser cette fois une couleur RGB.

```javascript
function draw()
{
    fill(200,50,5);
    rect(x,y,taille,taille);
}
```

Pour que notre demande de changement de couleur fonctionne, il faut l'effectuer avant de dessiner notre rectangle.
Vous pouvez rafraichir la page web, cette fois-ci le carré aura apparu.
Par défaut, il possède un contour noir qui n'est franchement pas beau. Nous allons le retirer avec d'autres fonctions de *configuration* (comme `fill`).
La fonction `noStroke`, litérallement *pas de contour* nous permet de retirer le contour de tout les éléments qui seront dessinés après l'instruction. Cette fonction ne prends pas de paramètres.

```javascript
function draw()
{
    fill(200,50,5);
    noStroke();
    rect(x,y,taille,taille);
}
```

### Mouvement
Excellent. Et si nous le faisions bouger maintenant ?
Tout ce que nous avons à faire, c'est modifier les valeurs de position durant notre boucle *draw*.
après l'affichage du rectangle, nous allons ajouter la ligne suivante :
```javascript
x++;
```

Cette instruction incrémente, donc ajoute 1, à la variable *x*. Ce qui signifie qu'à chaque image affichée, la position x augmentera de 1 pixel en x, et se déplacera donc sur la droite.

Si vous relancez votre page web, vous verrez l'équivalent d'un pinceau laissant une immonde trace rouge en avançant sur la droite.
Pourquoi ? Et bien parcequ'à chaque frame, nous dessinons un nouveau rectangle, mais nous n'effaçons pas ce que nous avons dessiné à la frame précédante !

Pour corriger cela, nous allons rajouter une instruction au début de la fonction draw, et celle-ci est la même qu'au début du programme : `background(0)`. Ainsi, à chaque frame, notre fond sera de retour à un noir complet.
Nous pouvons même utiliser notre variable pour la couleur de fond, afin de n'avoir qu'une seule valeur à modifier si nous souhaitons la changer.

Voici le code complet à ce stade :

```javascript
//constantes
const LARGEUR = 800;
const HAUTEUR = 600;

//variables globales
let x;
let y;
let taille;
let couleurFond;

function setup()
{
    couleurFond = 0;
    
    createCanvas(LARGEUR,HAUTEUR);
    background(couleurFond);
    
    x = LARGEUR / 2;
    y = HAUTEUR / 2;
    taille = 10;
}

function draw()
{
    background(couleurFond);
    
    fill(200,50,5);
    noStroke();
    rect(x,y,taille,taille);
    
    x++;
}
```

### Tests logiques
Tout ça c'est très bien, mais le carré nous quitte tristement et ne revient jamais.
Nous allons donc faire en sorte que lorsque le carré atteint le bord droit de l'écran, sa position soit changée en le bord gauche de l'écran.
Comment faire ça ? Avec des tests logiques. Nous connaissons la position x et la position maximum, puisque c'est la largeur de l'écran.
Voici à quoi ressemble un test logique

```javascript
if(expression booléenne est vrai)
{
    faire quelque chose
}
else
{
    faire autre chose
}
```
le mot clé `if`, tratuit *si*, est accompagné de parenthèses dans lesquels ont effectue un test logique, ou test booléen. Pourquoi booléen ? Car il utilise l'algèbre de boole.
C'est quoi que c'est-y dit-moi que ça, hein ?

#### Algèbre de boole
L'algèbre de boole est un système de calcul dont le résultat est soit **vrai**, soit **faux**. Si vous vous souvenez, plus haut, lors de la création de variables, j'ai créé l'instruction suivante `let c = true`. J'ai créé une varibale qui contient un booléen : *vrai*.

Dans l'algèbre de boole, on utilise des opérateurs différents des habituels `+ - * /`.

Opérateurs booléens principaux
------|-----------------------
==    | Compare deux valeurs, retourne vrai si les valeurs des deux côtés sont égales, faux sinon
<     | ce qui est à gauche est plus petit que ce qui est à droite
>     | ce qui est à gauche est plus grand que ce qui est à droite
!=    | L'inverse du premier, retourne vrai si les valeurs ne sont pas égales

Soit la situation suivante :

```javascript
let a = 2;
let b = (a == 2);
```

Vous pouvez voir les booléens comme des questions.
*Est-ce que a est égal à 2 ?*, si oui, l'expression retourne vrai, sinon, elle retourne faux. Et ce résultat est stockée dans *b*.

Voici quelques opérateurs supplémentaires qui nous serons utiles dans le futur.

Opérateurs booléens supplémentaires
-----|-----------------------------
`&&` | ET. Pour retourner vrai, les valeurs à gauche et à droite doivent être vrai
`||` | OU. Il faut que l'une des deux valeurs soit vrai que qu'il retourne vrai
`!`  | NON. inverse la condition

On peut faire plusieurs tests ensemble. Soit la situation suivante :

```javascript
let a = 2;
let b = 5;
let c = (a == 2 && b == 1)
```

Le test si-dessus retourne faux. car *a* est égale à 2, donc vrai à gauche, mais *b* n'est pas égal à 1, donc faux à droite.
*vrai* et *faux* donne faux. 

Nous aurons l'occasion d'utiliser chacun d'entre eux durant les excercice et de les réexpliquer en détail, avec des exemples concrêts.
[Plus sur l'algèbre de boole](https://fr.wikipedia.org/wiki/Alg%C3%A8bre_de_Boole)

De retour à nos tests logiques, il s'agit simplement de tester la valeur d'un booléen.
Dans notre cas, nous voulons la condition suivante :
*Si la position x est plus grande que la largeur, x doit valoir zéro. Sinon, x doit être incrémenté*

Qui se traduit en code par :

```javascript
if(x > LARGEUR)
{
    x = 0;
}
else
{
    x++;
}
```

Nous pouvons donc remplacer la partie *x++;* dans notre code actuel par le test ci-dessus.
Ainsi, tant que x est entre 0 et la largeur, il sera incrémenté de 1, sinon, il sera remis à 0.

Voici notre code actuel :

```javascript
//constantes
const LARGEUR = 800;
const HAUTEUR = 600;

//variables globales
let x;
let y;
let taille;
let couleurFond;

function setup()
{
    couleurFond = 0;
    
    createCanvas(LARGEUR,HAUTEUR);
    background(couleurFond);
    
    x = LARGEUR / 2;
    y = HAUTEUR / 2;
    taille = 10;
}

function draw()
{
    background(couleurFond);
    
    fill(200,50,5);
    noStroke();
    rect(x,y,taille,taille);
    
    if(x > LARGEUR)
    {
        x = 0;
    }
    else
    {
        x++;
    }
}
```

N'oubliez pas de commit vos modifications sur Github.

Félicitations ! Vous avez créé un cube qui parcours l'écran de gauche à droite.
Cet exercice vous à appris les bases de javascript.
Vous trouverai toutes les fonctions P5 sur sa [documentation](http://p5js.org/reference/).
Pour ce qui est de questions générales de javascript, votre moteur de recherche favoris devrait vous ouvrir les portes de [Stack Overflow](https://stackoverflow.com/), qui contient une réponse à tout.
Sinon, pour la documentation de base de Javascript, le [Mozilla Developper Network](https://developer.mozilla.org/en-US/docs/Web/javascript) devrait satisfaire toutes vos questions.

Dans les prochains tutoriels, nous aborderons des conceptes un peu plus complexes et un peu plus intéressants, comme les objets.
