Pacman
======

**Pacman** (non ce n'est pas une blague, les developpeurs étant de grands enfants) est le nom du gestionnaire de paquets. C'est un outil en ligne de commande très puissant puisqu'il peut tout installer ou presque., les paquets venant d'**Aur** (Arch User Repository) sont à parts et eux nécessitent d'utiliser un autre gestionnaire. En ce qui me concerne, depuis que **Yaourt** est mort (eh oui c'est pas encore une blague) ce sera **Yay** le bien nommé, très proche de feux Yaourt.



Synchronisation avec les dépôts de Manjaro
__________________________________________ 
 
C'est l'étape incontournable à faire en premier avant d'installer ou de mettre à jour la distribution. On synchronise la liste des dépôts locaux de notre ordinateur avec celui des serveurs. A ce stade, on suppose que vous avez soit choisi vos propres dépôts, généralement plus proches de chez vous et donc plus rapide soit la totalité des dépôts.

Une synchronisation normale se fait de cette manière

``sudo pacman -Sy``

Il arrive parfois que l'on est obligé de forcer cette synchronisation avec

``sudo pacman -Syy``


Mettre à jour le système
________________________

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


Rechercher un paquet
____________________

Pour cela, on va lancer une recherche avec un mot clé qui est généralement le nom du logiciel, même une partie de celui-ci ou encore sa description.

``pacman -Ss monlogicielrecherché``


Installer un logiciel
_____________________

Une fois le ou les paquet(s) trouvé(s) (sauf si on connaît déjà son nom), on peut l'installer de la manière suivante:

``sudo pacman -S monlogicieltrouvé unautrelogicieltrouvé``


Désinstaller un logiciel
________________________

La désinstallation classique se fait comme cela:

``sudo pacman -R monlogicielaenlever``


Parfois voir souvent, pacman a installé d'autres paquets comme dépendance du premier nécessaire à son bon fonctionnement. Il est alors utile de tout désinstaller en même temps et sans se souvenir/connaître le nom des ces paquets.

``sudo pacman -Rs monlogicielaenlever``

Pacman conservera lors de cette désinstallation une sauvegarde des fichiers de configurations du paquet en question au cas où l'on change d'avis ultérieurement. Si on ne veut pas que ce soit le cas, car on est sur de chez sur, dans ce cas la commande suivante sera passée.

``sudo pacman -Rsn monlogicielaenlever``

Dans le cas d'un logiciel et de ses dépendances qui peuvent poser problème (cela survient généralement lors d'une maj), on peut être obligé de faire:

``sudo pacman -Rdd qpdfview``


Information sur un paquet
_________________________

Pour une raison (un soucis) ou une autre (curiosité), on a besoin de savoir quel est la version de notre paquet installé.

``pacman -Qi popplet-qt5``


Si l'on veut connaître la liste des fichiers appartenant à un paquet, on utilise:

``pacman -Ql popplet-qt5``


Si on a un groupe de paquets installés qui commencent tous par monnompaquet-*.
Dans ce cas on peut faire comme pour virtualbox par exemple qui vient assez nombreux car on a:


* linux515-virtualbox-guest-modules
* linux515-virtualbox-host-modules
* virtualbox
* virtualbox-ext-oracle
* virtualbox-ext-vnc
* virtualbox-guest-iso
* virtualbox-guest-utils
* virtualbox-host-dkms
	
La solution serait de mettre dans une pipe qui recherchera tout ce qui concerne Virtualbox.

``pacman -Q | grep virtualbox``

.. NOTE:: Virtualbox est un cas à part mais si on a des problèmes on peut faire:
1. Ajouter $USER au groupe vboxuser
  * ``sudo gpasswd -a $USER vboxusers``
  
2. ``sudo vboxreload``
3. ``vboxmanage --version`` nous donne la version de virtualbox en cours


.. NOTE:: Pour connaître tous les services démarré de Virtualbox. ``systemctl status virtualbox``


Une autre commande fort utile est de savoir le nom des paquets orphelins. Ce sont des paquets qui n'ont plus de mainteneurs et dont la version commence à dater. 

``pacman -Qdt``

Parfois, on veut connaitre ce que fais/est un paquet (description, logiciels remplacés)

``pacman -Si xorgproto``


Nettoyer son cache
__________________

Par défaut, pacman conserve les paquets installés dans */var/cache/pacman/pkg*. Ce qui au bout d'un moment va vite devenir rempli. Il est donc necessaire de faire un peu le ménage de la manière suivante:


``sudo pacman -Sc``


On peut aussi vider entièrement le cache sans rien conserver.

``sudo pacman -Scc``


Installer un paquet hors dépôt
______________________________

Cette situation doit être exceptionnelle. Bien entendu, ni les dépôts de **Manjaro**, ni **AUR** ne peuvent nous aider. Elle peut survenir quand on a un soucis ou bien quand on a un besoin express de ce paquet. Dans ce cas, on crée un PKBUILD puis on crée le paquet. Et enfin, on installe ce paquet hors dépôt avec cette commande.

``sudo pacman -U cheminversmonpaquet/nomdupaquetcrée-any.pkg.tar.xz``


.. IMPORTANT:: Cette méthode à l'avantage d'installer et de désinstaller proprement le logiciel en question. C'est recommandé mais à faire le moins possible.

.. NOTE:: Le chemin est à adapter par rapport à l'endroit où vous avez ouvert votre terminal.