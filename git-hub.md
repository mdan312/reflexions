# Git Up

Système pour gérer les versions et le travail collaboratif
https://www.udacity.com/wiki/ud775/install-git

Autres systèmes: CVS qui a été amélioré en SVN (subversion) et Mercurial (HG) qui est similaire à GIT.  
SVN ne fonctionne pas offline.

## Installation

Dans propriétés de la fenêtre GIT BASH cocher case édition rapide pour bénéficier du copier coller par clic droit.  
Pour avoir la couleur (en N&B par défaut) et autres réglages:

	git config --global color.ui auto
	git config --global http.proxy proxy.cete-mediterranee.i2:8080
	git config --global core.editor "'C:/Program Files/EditPlus 3/EditPlus.exe' -n -w"
	git config --global core.editor vim
	git config --global push.default upstream
	git config --global user.name "DO"
	git config --global credential.helper wincred
	git config --global user.email you@example.com
	git config --global merge.conflictstyle diff3

## .bash_profile

Fichier script de config lancé à chaque démarrage à placer dans ~ (répertoire c:\users\[Nom User])
Y ajouter les définitions d'alias, du genre:

	alias edit="C:/Program\ Files/EditPlus\ 3/EditPlus.exe"
	alias asteroids="cd C:/huge/formation/ud775\ GIT/asteroids"

Ce fichier peut aussi servir à lancer des scripts shells, du genre git-prompt.sh et git-completion.bash



## Aide en ligne
Pour avoir la doc (styme `man`) d'une commande: `git help <command>`.  
exemple: `git help diff`.  

## Différences

La recherche de différence entre deux versions d'un fichier source permet de repérer les bogues et régressions.

fc
: outil standard de Windows

diff
: outil standard sur Mac et Linux

Windiff
: diff pour Windows


## git log --stat

ID, auteur, date, commentaire  
L'option --stat liste les fichiers modifiés et le nombre de modifs  
L'option --oneline liste seulemement ID et message

`q` pour quitter
## git diff

Par défaut compare fichiers du répertoire courant avec staging area. Si option `--stagged` compare staging area avec dernier commit

	git diff --staged

	git diff ID1 ID2 

`-` = ID1  
`+` = ID2

pour chaque modif: numéros de ligne et nb de lignes
`q` pour quitter

	git show ID

montre modifs par rapport au commit précédent

## git clone

Permet de rappatrier en local ou dupliquer localement

	git clone https://github.com/udacity/asteroids.git
	git remote -v

Si on veut lier un repository GitHub avec un dossier local

	git remote add origin [URL]
	git push origin master

permet d'avoir les infos sur repository origin

## git checkout ID

final: 3884eab839af1e82c44267484cf2945a766081f3 = master


## git init

Crée le dossier .git mais ne fait pas de commit

## git add -A

## git status

Permet de voir modifications non commitées

## git checkout 

	git checkout -- game.js

retour à la version du commit 

ou changement de branche 

	git checkout [branch]

##  git commit -m "[descriptive message]"

## git branch [nomBranche]

affiche les branches ou en crée une nouvelle

Affichage arbre:

	git log --graph [branche1] [branche2]
	git log --graph --oneline master coins

	git checkout -b nouvelleBranche

équivaut à `git branch` suivi d'un `git checkout`

## git merge master coins

1. se mettre dans la branche cible par `git checkout`
2. git merge master coins
3. en cas de bogue git merge --abort

## git fetch


git fetch = copie locale d'un dépot distant (toutes branches)

git pull origin master
=
git fetch origin 
+
git merge origin/master master

## URL de dossiers intéressants

<https://github.com/udacity/pappu-pakia.git>
<https://github.com/udacity/asteroids.git>

## git reset [commit]

permet de revenir au commit (on supprimer commits ultérieurs)
Les fichiers du répertoire de travail ne sont pas modifiés

git reset --hard 

Annule les mises à jour des fichiers du répertoire de travail depuis le commit

