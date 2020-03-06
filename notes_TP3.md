# Compte-rendu TP n°3 : Gestion des paquets
		
## EXERCICE 1

1. Quels sont les 5 derniers paquets installés sur votre machine ?
La commande *cat /var/log/apt/history.log* nous permet d'obtenir les 5 derniers paquets

2. 
En utilisant *dpkg* et *apt* pour compter le nombre de paquets installés nous arrivons à 572 paquets avec la commande *apt-cache stats* et 549 paquets avec la commande *dpkg --get-selections | wc -l*

3.

4. On utilise la commande *alias maj='apt-get upgrade*.

5.*sudo apt install fortunes*. Ce paquet sert a afficher des citations amusantes.

6.'apt-cache search sudoku'

Il y a : "fltk1.1-games - Fast Light Toolkit - example games: checkers, sudoku" et beaucoup d'autres.



## EXERCICE 2

Pour obtenir des informations sur **ls** en une commande: *dpkg -S $(which ls)*


**origine-commande**
'''bash
dpkg -S $(which $1)
'''

## EXERCICE 3
**test-installed**

'''bash
nbpaquet=$(dpkg -l $1 2>/dev/null | wc -l)

if [ $nbpaquet == "0" ] ; then
	echo "NON INSTALLÉ"
else
	echo "INSTALLÉ"
fi
'''

## EXERCICE 4

Voici la commande permettant d'obtenir la liste des programmes livrés avec coreutils *dpkg -L coreutils*

``[ ``: alias de 'test' permet de tester une expression

on peut afficher ce qu'elle retourne avec echo $``[`` expression ``]``

## EXERCICE 5

On commence par ouvrir aptitude, ensuite on utilise 'Ctrl + T', on cherche emacs dans la liste des paquets disponibles puis on l'ajoute aux paquets à installer avec '+' ensuite on installe avec 'G' puis 'G'.

## EXERCICE 6

On installe la version Oracle de Javec grâce aux commandes suivantes
	sudo add-apt-repository ppa:linuxuprising/java
	sudo apt update
	sudo apt install oracle-java11-installer
Suite à ces commandes un nouveau fichier a été créé dans /etc/apt/sources.list.d le fichier linuxuprising-ubuntu-java-eoan.list , ce fichier contient les adresses des PPA.

## EXERCICE 7

En ayant suivis toutes les instructions nous avons réussi à créer un nouveau paquet. Pendant cet exercice nous nous sommes rendu compte de l'importance du répertoire courant utilisé par les commandes, ainsi que de l'importanc de la syntaxe dans les fichiers décrivant les paquets (distributions par exemple).
