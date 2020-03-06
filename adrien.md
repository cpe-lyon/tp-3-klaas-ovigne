# Compte-rendu TP n°3 : Gestion des paquets
		
## EXERCICE 1

1. Quels sont les 5 derniers paquets installés sur votre machine ?

On utlise `grep " install " /var/log/dpkg.log | tail -5`

&nbsp;

2. Utiliser **dpkg** et **apt** pour compter le nombre de paquets installés (ne pas hésiter à consulter le manuel !). Comment explique-t-on la (petite) différence de comptage ?

En utilisant *dpkg* et *apt* pour compter le nombre de paquets installés nous arrivons à : 
- 572 paquets avec la commande ``apt-cache stats`` 
- 549 paquets avec la commande ``dpkg --get-selections | wc -l``

&nbsp;

3. Combien de paquets sont disponibles en téléchargement ?

On utilise : ``apt list |wc -l`` On a donc 61599 paquets disponibles en téléchargement.

&nbsp;

4. Créer un alias "**maj**" qui met à jour le système

On utilise : ``alias maj='apt-get upgrade``

&nbsp;

5. A quoi sert le paquet **fortunes** ? Installez-le.

Ce paquet sert a afficher des citations de manière aléatoire.
Pour l'installer, on fait : ``sudo apt install fortunes``

&nbsp;

6. Quels paquets proposent de jouer au sudoku ?

Pour afficher ces paquets, on utilise : `apt-cache search sudoku`

Il y a : "fltk1.1-games - Fast Light Toolkit - example games: checkers, sudoku" et bcp d'autres.

&nbsp;

7. Lister les derniers paquets installés explicitement avec la commande **apt install**

On utilise `apt list --manual-installed`

&nbsp;

## EXERCICE 2

1. A partir de quel paquet est installée la commande ls ? Comment obtenir cette information en une seule
commande, pour n’importe quel programme?

Afin de trouver a partir de quel paquet la commande ls est installée, on fait : ``dpkg -S $(which ls)``

&nbsp;

2. Utilisez la réponse à pour écrire un script appelé origine-commande (sans l’extension.sh) prenant en argument le nom d’une commande, et indiquant quel paquet l’a installée.

**origine-commande**
```bash
dpkg -S $(which $1)
```

On pourra alors trouver dans quel paquet est installée n'importe quelle commande grâce a ce script. (exemple : ``origine-commade ls``
&nbsp;

## EXERCICE 3
**test-installed**

```bash
nbpaquet=$(dpkg -l $1 2>/dev/null | wc -l)

if [ $nbpaquet == "0" ] ; then
	echo "NON INSTALLÉ"
else
	echo "INSTALLÉ"
fi
```

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
