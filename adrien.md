# Compte-rendu TP n°3 : Gestion des paquets
		
## EXERCICE 1

1. Quels sont les 5 derniers paquets installés sur votre machine ?


&nbsp;

2. Utiliser **dpkg** et **apt** pour compter le nombre de paquets installés (ne pas hésiter à consulter le manuel !). Comment explique-t-on la (petite) différence de comptage ?



&nbsp;

3. Combien de paquets sont disponibles en téléchargement ?

On utilise : ``apt list |wc -l`` On a donc 61599 paquets disponibles en téléchargement.

&nbsp;

4. Créer un alias “**maj**” qui met à jour le système

'alias maj='apt-get upgrade''

&nbsp;

5. A quoi sert le paquet **fortunes** ? Installez-le.

'sudo apt install fortunes'
il sert a afficher des citations cocasses.

&nbsp;

6. Quels paquets proposent de jouer au sudoku ?


'apt-cache search sudoku'

il y a : "fltk1.1-games - Fast Light Toolkit - example games: checkers, sudoku" et bcp d'autres.

&nbsp;

7. Lister les derniers paquets installés explicitement avec la commande **apt install**


&nbsp;

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
