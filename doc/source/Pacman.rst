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



