#Tutoriel Javascript P5 orienté objects

Ce tutoriel est une introduction au javascript et au framework P5, le tout orienté objets.

*Disclaimer : Je ne prétends pas être un expert en la matière. Je réalise ce tutoriel basé sur mes connaissances, qui peuvent ne pas être complètes ou à jour.*

##Qu'est-ce qu'un framework

> Un framework désigne un ensemble de composants logiciele qui servent à créer les fondations ainsi que les grandes lignes d'un logiciel.
[Wikipedia](https://fr.wikipedia.org/wiki/Framework "Page Wikipedia sur les framework")

En gros, ce sont des fonctions écrites par des gens sympatiques sur lesquels nous pouvons nous baser pour réaliser nos applications afin de nous faciliter la vie.

Exemple : le framework P5, axé sur la création de contenus graphiques sur une page HTML.
Au lieu de créer des éléments HTML de type canvas et de s'embêter avec tout les paramètres et les syntaxes complexes, ce framework possède des fonctions adaptées, comme `createCanvas(width,height);` qui créé un canvas HTML automatiquement à notre place.

##Pourquoi P5

Il existe une multitude de framerowk Javascript et tout le monde a ses préférences.
J'ai découvert P5 grâce à des challenge de code sur Internet réalisés par [Daniel Shiffman](http://thecodingtrain.com/ "Site de Daniel Shiffman").
C'est un très bon framework pour créer du contenu graphique, mais il est très jeune, ce qui a des avantages et des inconvéniants.

##Environnement de développement

Il est important d'avoir un environnement de développement stable dans lequel on se sent à l'aise pour coder.
Afin de pouvoir travailler sur nos projets depuis partout, il est aussi une bonne idée de posséder un compte Github. Nous en reparlerons sous peu.

###Editeur de code

L'éditeur de code de choix, pour ma part, est [Visual Studio Code](https://code.visualstudio.com/ "Sit web du VS Code"), développé par Microsoft. Il est simple d'utilisation, multi-plateforme, intègre une bibliothèque de plugins et une interface graphique pour Git (nous en reparlerons plus tard)

###Gestionnaire de version

Git est un logiciel de [versionning](https://en.wikipedia.org/wiki/Software_versioning "Page Wikipedia sur le versionning (EN)"). Nous ne l'utiliserons pas seul, mais en association avec la plateforme Github, qui permet de stocker des projets gratuitement tant que ceux-ci sont open source. Git nous permettra d'envoyer notre code depuis l'éditeur de code à Github en quelques cliques.
Le but ici est dans un premier temps de stocker notre code en ligne pour y accéder partout, mais Github est avant tout une plateforme de contribution. Si vous commencez un projet plus ambitieux, d'autres personnes pourrons participer à votre projet open source au travers de Github.

###Navigateur

Notre but est de créer des applications web, et pour cela, nous aurons besoin d'un navitateur (logique).
Mes conseils : Si  vous êtes sous Windows, utilisez Chrome, si vous êtes sur Linux, utilisez Firefox.

Chrome est l'un des navigateurs les plus utilisés et supporte toutes les dernières technologies. De plus, il fonctionne très bien derrière un proxy sur Windows, comparré à Firefox, qui a tendance à faire de la merde.

Firefox est tout aussi bien que Chrome, et est installé de base sur Linux.

###Serveur Web

Nous utiliserons un serveur web local pour développer nos applications. Il est important d'en utiliser un, car cela permet de voir le *vrai* résultat final, comme si le site était réellement hébergé en ligne.
Cela permet notemment de bypass une sécurité présente dans les navigateurs empêchant un fichier javascript de charger des images depuis le disque.

En hébergeant le site web, même en local, cette sécurité tombe, puisque les images sont désormais chargées depuis un serveur.

Nous utiliserons XAMPP sur Windows, et LAMP sur Linux pour créer notre serveur web.

##Installation et configuration de l'environnement

###Windows 10

###Git

La première étape est de télécharger Git pour Windows. Rendez-vous sur le [site de Git](https://git-scm.com/download/win "Page de téléchargement de Git pour Windows") et enregistrez le fichier exe.
Lancez l'installation avec les paramètres par défaut (sauf si vous vous y connaissez, mais dans ce cas : pourquoi lisez-vous ce tutoriel ?)
Je vous conseille juste d'utiliser l'option "Use Git from the Windows Command Prompt" afin d'avoir accès aux commandes depuis une console Powershell, par exemple.

Justement, ouvrez une console Powershell et tapez les commandes suivantes, en remplaçant les champs par vos informations Github, afin que Git vous connaisse.
```bash
git config --global user.name "<pseudo Github>"
git config --global user.email <email Github>
```

Cette partie est importante pour plus tard.

###Visual Studio Code

Une fois Git installé, rendez-vous sous le [site de VS Code](https://code.visualstudio.com/docs/?dv=win "Téléchargement de VS Code") et téléchargez l'executable.
Suivez les instructions d'installation et gardez les options de base.

###Google Chrome
Rendez vous sur le [site de Google Chrome](https://www.google.com/chrome/browser/thankyou.html?platform=win64&statcb=1&installdataindex=defaultbrowser "Téléchargement de Google Chrome") et téléchargez l'installateur.
Lancez-le.

###XAMPP

Récupérez l'installeur de [XAMPP pour Windows](https://www.apachefriends.org/xampp-files/7.1.1/xampp-win32-7.1.1-0-VC14-installer.exe "Téléchargement de XAMPP") et lancez le setup.
Nous n'aurons beosin que d'Apache, vous pouvez donc désactiver tout les autres services.

Cette étape n'est pas requise si vous ne souhaitez pas charger des fichiers images en JS, mais je vous recommande vivement de le faire.


##Github

Félicitation ! Vous avez maintenant terminé l'installation de votre environnement de développement.
Nous allons maintenant créer un compte sur Github afin de pouvoir y stocker notre code.

Rendez-vous sur [Github](https://github.com/ "Site de Github") et créez un nouveau compte. Utilisez votre adresse email personnel (pas une adresse poubelle), c'est important.
Une fois le compte créé, vous êtes prêts à créer votre premier projet.
Rendez-vous sur la page de [nouveau projet](https://github.com/new "Page 'new project'") et renseignez un nom. Par exemple : **jsHelloWorld**

Gratuitement, vous ne pouvez créer que des dépots publiques. Ce n'est pas un problème dans notre cas.
Cochez la case *Initialize this repository with a README* qui créera un fichier *Lisez-moi* dans le dépot.

Vous pouvez maintenant créer le dépot.

##Premier projet

Vous avez maintenant créé un dépot Github vide. Enfin, pas vraiment vide, il contient un fichier README.

Nous allons maintenant localiser notre web server.
Dans le dossier d'insllation de XAMPP (à la racine C:, ou dans Program Files) se trouve un dossier nommé *htdocs*.
Dans ce dossier, nous allons créer un dossier nommé *projets*.

Lorsque vous aurez lancé le service Apache depuis le panneau de contrôle XAMPP, ce dossier sera accessible par votre navigateur avec l'URL `localhost/projets/`.
Nous allons maintenant remplir ce dossier.

Retournez sur la page Github de votre projet fraichement créé.
Sur la page du dépot, cliqze sur *Clone or download* et récupérez le lien HTTPS de clonage.

Lancez Git GUI (la version avec interface graphique).
Cliquez sur *Clone Existing Repository* qui va nous permettre de cloner notre dépot git en local afin de travailler dessus.

Dans la source, collez le lien copié sur Github. Dans la cible, collez le lien vers le dossier créé précédement et ajoutez le nom du dépot github, par exemple `C:\xampp\htdocs\projets\jsHelloWorld\`.
Cliquez sur *Clone*. Lorsqu'il aura fini, vous pourrez fermer le programme.

Retournez dans votre explorateur de fichier et faites un clique droit sur le dossier *jsHelloWorld* créé par Git. Sélectionnez *Open with Code*, qui va ouvrir le dossier dans Visual Studio Code
Une fois ouvert, vous devriez remarquer la présence d'un fichier README dans le dossier. C'est le signe que notre dépot a été cloné.

Nous allons maintenant créer un fichier dans notre projet.
Faites un clique droit dans l'explorateur de VS Code et choisissez "Nouveau fichier".
Nommez-le *index.html*.
Entrez une ligne de texte dedans, par exemple `<!DOCTYPE html>`.
Enregistrez le fichier.

Vous aurez remarqué un petit **1** présent sur le troisième onglet à droite. Il s'agit de l'onglet Git. Cliquez dessus.
Il vous présente les fichiers qui ont été modifiés, et qui sont en attente de validation.
Cliquez sur le petit plus, à droite du fichier *index.html* pour l'ajouter aux modifications acceptées. Vous devrez également entrer un message dans la case au dessus, décrivant vos changements.
Ecrivez un texte dans le genre *Premier commit*.

Mais qu'est-ce qu'un commit ? C'est l'action que nous allons effectuer juste après.
Appuyez sur ctrl+Enter pour valider. Le fichier a disparu, ainsi que votre message.

Vous pouvez maintenant cliquer les trois petits points *Plus*s puis sur *Transferez (Push) Vers*.
Une proposition aura apparu au millieu en haut de l'écran, nommé *Origin* suivi d'une URL Githb.
VS Code vous demandera vos identifiants Github afin de pouvoir envoyer le code.

Et wala ! Vous avez effectué un commit.

###Ubuntu 16.04
*Todo*
