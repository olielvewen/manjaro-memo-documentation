Pacman
======

**Pacman** (non ce n'est pas une blague, les developpeurs étant de grands enfants) est le nom du gestionnaire de paquets. C'est un outil en ligne de commande très puissant puisqu'il peut tout installer ou presque., les paquets venant d'**Aur** sont à parts et eux nécessitent d'utiliser un autre gestionnaire. En ce qui me concerne, depuis que **Yaourt** est mort (eh oui c'est pas encore une blague) ce sera **Yay** le bien nommé, très proche de feux Yaourt.


### Synchronisation avec les dépôts de Manjaro
C'est l'étape incontournable à faire en premier avant d'installer ou de mettre à jour la distribution. On synchronise la liste des dépôts locaux de notre ordinateur avec celui des serveurs. A ce stade, on suppose que vous avez soit choisi vos propres dépôts, généralement plus proches de chez vous et donc plus rapide soit la totalité des dépôts.

Une synchronisation normale se fait de cette manière

``sudo pacman -Sy``

Il arrive parfois que l'on est obligé de forcer cette synchronisation avec

``sudo pacman -Syy``


### Mettre à jour le système

Le commande de base est 

``sudo pacman -Su``

Si les mainteneurs des paquets ont fait régréssé certains de ceux-ci, il est utilse de faire alors

``sudo pacman -Suu``


.. WARNING:: On peut faire à la fois et en même temps la synchronisation des dépots et la MAJ. C'est d'ailleurs ce que l'on fait en fait tout le temps. Une seule opération au lieu de deux.
Dans ce cas, ce sera 
``sudo pacman -Syu``

.. WARNING:: C'est la même chose qu'avec toutes les commandes précédantes
``sudo pacman -Syyu``
``sudo pacman -Syyuu``


### Rechercher un paquet

Pour cela, on va lancer une recherche avec un mot clé qui est généralement le nom du logiciel, même une partie de celui-ci ou encore sa description.

``pacman -Ss monlogicielrecherché``


### Installer un logiciel

Une fois le ou les paquet(s) trouvé(s) (sauf si on connaît déjà son nom), on peut l'installer de la manière suivante:

``sudo pacman -S monlogicieltrouvé unautrelogicieltrouvé``


### Désinstaller un logiciel

La désinstallation classique se fait comme cela:

``sudo pacman -R monlogicielaenlever``


Parfois voir souvent, pacman a installé d'autres paquets comme dépendance du premier nécessaire à son bon fonctionnement. Il est alors utile de tout désinstaller en même temps et sans se souvenir/connaître le nom des ces paquets.

``sudo pacman -Rs monlogicielaenlever``

Pacman conservera lors de cette desinstallation une sauvegarde des fichiers de configurations du paquet en question au cas où l'on change d'avis ultérieurement. Si on ne veut pas que ce soit le cas, car on est sur de chez sur, dans ce cas la commande suivante sera passée.

``sudo pacman -Rsn monlogicielaenlever``


