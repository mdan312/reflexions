# Git Up

Système pour gérer les versions et le travail collaboratif
https://www.udacity.com/wiki/ud775/install-git

Excellent survol de GIT
https://try.github.io/levels/1/challenges/1


Autres systèmes: CVS qui a été amélioré en SVN (subversion) et Mercurial (HG) qui est similaire à GIT.  
SVN ne fonctionne pas offline.

## Installation

Dans propriétés de la fenêtre GIT BASH cocher case édition rapide pour bénéficier du copier coller par clic droit.  
Pour avoir la couleur (en N&B par défaut), un proxy, des commandes personnalisées et autres réglages:

	git config --global color.ui auto
	git config --global http.proxy proxy.cete-mediterranee.i2:8080
	git config --global core.editor "'C:/Program Files/EditPlus 3/EditPlus.exe' -n -w"
	git config --global core.editor vim
	git config --global push.default upstream
	git config --global user.name "DO"
	git config --global credential.helper wincred
	git config --global user.email you@example.com
	git config --global merge.conflictstyle diff3
	git config --global core.autocrlf false
	git config --global alias.wdiff "diff --color-words"
	git config --global alias.wshow "show --color-words"

## .bash_profile

Fichier script de config lancé à chaque démarrage d'un shell bash, à placer dans ~ (répertoire c:\users\[Nom User])
Y ajouter les définitions d'alias, du genre:

	alias edit="C:/Program\ Files/EditPlus\ 3/EditPlus.exe"
	alias asteroids="cd C:/huge/formation/ud775\ GIT/asteroids"

Ce fichier peut aussi servir à lancer des scripts shells, du genre git-prompt.sh et git-completion.bash



## Aide en ligne
Pour avoir la doc (style `man`) d'une commande: `git help <command>`.  
exemple: `git help diff`.  

## Différences

La recherche de différence entre deux versions d'un fichier source permet de repérer les bogues et régressions.

fc
: outil standard de Windows 7

diff
: outil standard sur Mac et Linux

Windiff
: diff pour Windows


## git log --stat

ID, auteur, date, commentaire  
L'option --stat liste les fichiers modifiés et le nombre de modifs  
L'option --summary liste les fichiers modifiés et le nombre de modifs  
L'option --oneline liste seulemement ID et message

`q` pour quitter (on a certaines options de vim comme la recherche par /search)

## git diff

Par défaut compare fichiers du répertoire courant avec staging area (fichiers prêts à être commités). Si option `--stagged` compare staging area avec dernier commit

	git diff --staged

	git diff ID1 ID2 

`-` = ID1  
`+` = ID2

pour chaque modif: numéros de ligne et nb de lignes
`q` pour quitter

	git show ID

montre modifs par rapport au commit précédent

	git diff --color-words
	git show --color-words



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

ajoute fichiers à staging area
git reset <filename> = supprime fichiers de staging area

git checkout -- octocat.txt 

annule modifs sur fichier depuis dernier commit

## git status

Permet de voir modifications non commitées

## git checkout 

	git checkout -- game.js

retour à la version du commit 

ou changement de branche 

	git checkout [branch]

ou pour partir d'un ancien noeud

	git checkout -b new_branch_name



##  git commit -am "[descriptive message]"

-a ajoute les fichiers à la stagging area et tient compte des fichiers supprimés.

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

git push -u origin master

-u : mémoriser 

## git reset [commit]


permet de revenir au commit (on supprimer commits ultérieurs)
Les fichiers du répertoire de travail ne sont pas modifiés

	git reset [commit] --hard 

Annule les mises à jour des fichiers du répertoire de travail depuis le commit

## pull request

le commit indique le numéro de pull request, le nom de la branche

## mettre à jour son fork

git remote add upstream https://github.com/kushsolitary/pappu

## hooks

sorte de triggers permettant par exemple la mise à jour sur site ftp pour chaque push

http://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks

## git stash

permet de stocker fichiers édités mais non commités

`git stash apply` permet de récupérer ces fichiers édités après un pull

## merge Conflit

Bien tout commiter avant le merge
git merge --abort
revient à état initial après qu'un merge ait échoué (équivaut à git reset --hard)

Les commandes suivantes aident à voir là où ça bloque et d'où vient le problème:

	git wdiff master change <name of file>
	git log --merge --color-words -p <name of file>

L'éditeur suivant permet de voir les 3 versions:

	git mergetool --tool=vimdiff


L'outil `git reverse` fonctionne à l'inverse de git `cherry-pick`
