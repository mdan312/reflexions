# Git Up

Syst�me pour g�rer les versions et le travail collaboratif
https://www.udacity.com/wiki/ud775/install-git

Autres syst�mes: CVS qui a �t� am�lior� en SVN (subversion) et Mercurial (HG) qui est similaire � GIT.  
SVN ne fonctionne pas offline.

## Installation

Dans propri�t�s de la fen�tre GIT BASH cocher case �dition rapide pour b�n�ficier du copier coller par clic droit.  
Pour avoir la couleur (en N&B par d�faut) et autres r�glages:

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

Fichier script de config lanc� � chaque d�marrage � placer dans ~ (r�pertoire c:\users\[Nom User])
Y ajouter les d�finitions d'alias, du genre:

	alias edit="C:/Program\ Files/EditPlus\ 3/EditPlus.exe"
	alias asteroids="cd C:/huge/formation/ud775\ GIT/asteroids"

Ce fichier peut aussi servir � lancer des scripts shells, du genre git-prompt.sh et git-completion.bash



## Aide en ligne
Pour avoir la doc (styme `man`) d'une commande: `git help <command>`.  
exemple: `git help diff`.  

## Diff�rences

La recherche de diff�rence entre deux versions d'un fichier source permet de rep�rer les bogues et r�gressions.

fc
: outil standard de Windows

diff
: outil standard sur Mac et Linux

Windiff
: diff pour Windows


## git log --stat

ID, auteur, date, commentaire  
L'option --stat liste les fichiers modifi�s et le nombre de modifs  
L'option --oneline liste seulemement ID et message

`q` pour quitter
## git diff

Par d�faut compare fichiers du r�pertoire courant avec staging area. Si option `--stagged` compare staging area avec dernier commit

	git diff --staged

	git diff ID1 ID2 

`-` = ID1  
`+` = ID2

pour chaque modif: num�ros de ligne et nb de lignes
`q` pour quitter

	git show ID

montre modifs par rapport au commit pr�c�dent

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

Cr�e le dossier .git mais ne fait pas de commit

## git add -A

## git status

Permet de voir modifications non commit�es

## git checkout 

	git checkout -- game.js

retour � la version du commit 

ou changement de branche 

	git checkout [branch]

##  git commit -m "[descriptive message]"

## git branch [nomBranche]

affiche les branches ou en cr�e une nouvelle

Affichage arbre:

	git log --graph [branche1] [branche2]
	git log --graph --oneline master coins

	git checkout -b nouvelleBranche

�quivaut � `git branch` suivi d'un `git checkout`

## git merge master coins

1. se mettre dans la branche cible par `git checkout`
2. git merge master coins
3. en cas de bogue git merge --abort

## git fetch


git fetch = copie locale d'un d�pot distant (toutes branches)

git pull origin master
=
git fetch origin 
+
git merge origin/master master

## URL de dossiers int�ressants

<https://github.com/udacity/pappu-pakia.git>
<https://github.com/udacity/asteroids.git>

## git reset [commit]

permet de revenir au commit (on supprimer commits ult�rieurs)
Les fichiers du r�pertoire de travail ne sont pas modifi�s

git reset --hard 

Annule les mises � jour des fichiers du r�pertoire de travail depuis le commit

