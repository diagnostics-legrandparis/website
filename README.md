# Installation

# Prepare PowerShell

Démarre un Windows PowerShell en mode Admin (Touch windows + cherche Powershell + clique droit éxecuter en temps qu'admin)

# Installation de choco

chocolatey permet d'installer des logiciels facilement:
- https://chocolatey.org/install
- copie + colle la commande donné dans le PowerShell

# Install git, vscode, et hugo

Dans un PowerShell en mode Admin:
- choco install vscode
- choco install git
- choco install hugo

# Install github desktop

https://desktop.github.com/

# Télécharge le code

Dans github desktop:
- connect a github
- File -> clone repository -> onglet GitHub.com -> Select diagnostics-legrandparis/website -> Change local path pour celui que tu veux

# Modifier le site et le compiler

Ouvrir l'explorateur windows sur le dossier du site web (Dans github desktop -> Repository -> Show in explorer).
Faire clic droit -> Ouvrir avec Code

Configs/ -> Contient la configuration et le choix des couleurs
Content/ -> Contient tout le texte du site web
diagnostics-legrandparis.github.io/ -> Contient le code du site une fois compiler

## Tester localement

Ouvrir un terminal: dans vscode -> Terminal -> New Terminal

Dans le terminal:
`hugo server -D`

Le site est disponible dans le navigateur: http://localhost:1313/


## Modifier le vrai site web

Pour compiler le site:

- Dans le terminal: `hugo -D -d diagnostics-legrandparis.github.io/`
- Dans github desktop
