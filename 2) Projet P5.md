# Projet P5
Dans ce chapitre, nous allons voir la constitution d'un projet P5.

## Fichiers
Pour commencer, nous allons répurérer la librairie P5 sur le site officiel.
Voici un [lien direct](https://github.com/processing/p5.js/releases/download/0.5.8/p5.min.js "Librairie P5") vers la version complete et compressée.

Enregistrez ce fichier à la racine de votre projet Git, créé durant [l'introduction]("./1) Introduction.md").
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
`<script src="sketch.js"></script>` de la même manière, nous incluons ici un fichier *sketch.js*, qui n'existe pas encore.

Nous allons le créer maintenant, de la même manière que pour le fichier html.
> Astuce : vous pouvez également faire *ctrl+clic* sur le nom du fichier dans la balise html, vs code vous dira qwe le fichier n'existe pas et vous proposera de le créer.

--- a suivre

## Structure Javascript
