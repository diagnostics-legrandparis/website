# Architecture et explications

Un site web est composé de fichier de code:
- html: la structure du site web
- css: pour l'organisation et l'affichage 
- js: pour tout ce qui dynamique (ouverture de popup etc)

Modifier ces fichiers de code n'est pas facile. C'est pour ça que le site web est séparé en deux:
le code du site et le vrai site.

Le code du site contient des fichiers de types .md (format markdown) qui sont facilement modifiable
pour les humains (dans le dossier content) et le code qui permet de générer le vrai site qui est complexe mais dont on a rarement le besoin de modifier. 

Le problème c'est que ce code du site n'est pas utilisable tel quel par les navigateurs, il faut
alors le "compiler" et le transformer en vrai site web.

## Hugo

Hugo c'est le logiciel qui permet de compiler le code du site (qui est au format attendu par hugo) en vrai site web.

## VSCode ou Code

C'est un éditeur de texte fait pour le code. C'est plus facile de l'utiliser parce qu'il applique des couleurs pour lire plus facilement. Il colore aussi les changements en orange ou vert ve qui aide.

## Git

Git c'est une sorte de Google Drive/Dropbox mais pour le code. Ça fonctionne avec des repositories (ou dépôt) qui contiennent les fichiers du code:
- https://github.com/diagnostics-legrandparis/diagnostics-legrandparis.github.io est le repository du vrai site web
- https://github.com/diagnostics-legrandparis/website est le repository du code source

Dans notre cas, ils sont stocké via Github qui est un server de repositories (mais il en existe plein d'autres). On utilise github parce qu'il est capable d'aussi herberger un site web.

Git fonctionne avec des commits. Un commit est un changement sur un ou plusieurs fichier. Si tu changes 3 pages de ton siteweb, a la fin tu pourras faire un commit du changement contenant tous ces changements. L'intérêt de git c'est de pouvoir connaitres tous les changements sur le site web et pouvoir les retirer ou modifier si il y a un problème. Ça permet aussi de voir qui a modifier quoi et quand.

Quand on utilise git, on fait une copie local du repository et on le maintient synchronisé avec des push et des pull/fetch. Lorsque qu'on fait une modification, il faut faire un commit puis le push sur le server. Si quelqu'un d'autre fait un changement sur le server il faut pull/fetch son changement locallement pour éviter de l'écraser plus tard. 


# Installation

## Prepare PowerShell

Démarre un Windows PowerShell en mode Admin (Touch windows + cherche Powershell + clique droit éxecuter en temps qu'admin)

## Installation de choco

chocolatey permet d'installer des logiciels facilement:
- https://chocolatey.org/install
- copie + colle la commande donné dans le PowerShell

## Install git, vscode, et hugo

Dans un PowerShell en mode Admin:
- choco install vscode
- choco install git
- choco install hugo

## Install github desktop

https://desktop.github.com/

# Télécharge le code

Dans github desktop:
- connect a github
- File -> clone repository -> onglet GitHub.com -> Select diagnostics-legrandparis/website -> Change local path pour celui que tu veux

Ouvrir l'explorateur windows sur le dossier du site web (Dans github desktop -> Repository -> Show in explorer).
Faire clic droit -> Ouvrir avec Code

Ouvrir un terminal dans VsCode: dans vscode -> Terminal -> New Terminal
Dans le terminal:
`git submodule update --init`

Retourner sur github desktop:
- File -> Add local repository -> retrouver le repository website précendement créé ("website") -> ouvrir website et selectionner le dossier `diagnostics-legrandparis.github.io` -> Cliquer sur Add repository


# Modifier le site et le compiler

IMPORTANT: Toujours aller sur github desktop avant et cliquer sur fetch origin en haut. Ça permet de télécharger les changements fait depuis un autre ordinateur

Ouvrir l'explorateur windows sur le dossier du site web (Dans github desktop -> Repository -> Show in explorer).
Faire clic droit -> Ouvrir avec Code

Architecture des dossiers:
- Configs/ -> Contient la configuration et le choix des couleurs
- Content/ -> Contient tout le texte du site web
- diagnostics-legrandparis.github.io/ -> Contient le code du site une fois compilé

## Tester localement

Ouvrir un terminal: dans vscode -> Terminal -> New Terminal

Dans le terminal:
`hugo server -D`

Le site est disponible dans le navigateur: http://localhost:1313/


## Modifier le vrai site web

Une fois tester les changements, on peut compiler et enregistrer le site web:

- Compiler le site web -> Dans le terminal: `hugo -D -d diagnostics-legrandparis.github.io/`

### Enregistrer/Uploader le site web:

dans github desktop:
- Mettre current repository sur diagnosctics-legrandparis.github.io
- Il va y avoir plein de fichiers changers incomprehensibles, c'est normal
- En bas du menu de gauche il y a un bouton "commit", remplir le champs summary
avec un resumé en quelque mot de la nature du changement (Exemple: "Mise a jour de la page contact avec XX modif"), cliquer sur Commit et Push origin (en haut a droite). Le vrai site web sera alors modifié
- Mettre current repository sur website
- Verifier que les changements dans les fichiers sont bon (verifier les fautes d'orthographes, si il n'y a pas des mots oubliés etc)
- Faire le commit de la même manière que pour le précedent repository (ne pas oublier push origin)
