# Compte-rendu TP n°3 : Gestion des paquets
		
## EXERCICE 1

1. Quels sont les 5 derniers paquets installés sur votre machine ?

'cat /var/log/apt/history.log' : 5 derniers paquets : mlocate, + majs en tt genres

2. apt-cache stats               572
dpkg --get-selections | wc -l    549

3.

4.'alias maj='apt-get upgrade''

5.'sudo apt install fortunes'
il sert a afficher des citations cocasses.

6.'apt-cache search sudoku'

il y a : "fltk1.1-games - Fast Light Toolkit - example games: checkers, sudoku" et bcp d'autres.



			EXERCICE 2

en une commande: 'dpkg -S $(which ls)'


**origine-commande**
'''bash
dpkg -S $(which $1)
'''

			EXERCICE 3
**test-installed**

'''bash
nbpaquet=$(dpkg -l $1 2>/dev/null | wc -l)

if [ $nbpaquet == "0" ] ; then
	echo "NON INSTALLÉ"
else
	echo "INSTALLÉ"
fi
'''

			EXERCICE 4

liste des pgr livrés ac coreutils ; 'dpkg -L coreutlis'

[ : alias de 'test' permet de tester une expression

on peut afficher ce qu'elle retourne avec echo $[ expression ]

			EXERCICE 5

ouvrir aptitude
chercher emacs (editors->emacs)
'+' ou 'Ctrl + T' -> Paquet -> Installer puis 'G' puis 'G'

			EXERCICE 6

sudo add-apt-repository ppa:linuxuprising/java
sudo apt update
sudo apt install oracle-java11-installer

dans /etc/apt/sources.list.d il y a : linuxuprising-ubuntu-java-eoan.list ds ce fichier il a les adresses des PPA.