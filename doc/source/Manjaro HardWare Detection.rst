Manjaro HardWare Detection
==========================


**Manjaro HardWare Detection** ou plutôt **mhwd** comme on va l’appeler dorénavant est un outil propre à **Manjaro**. Sous cette appellation se cache en fait deux outils assez sympas en CLI mais aussi de manière graphique.

- **mhwd** : est la commande de base, active dés le début qui permet la détection et la configuration du hardware qu'il soit pci ou usb.

Noter que cet outil est encore en développement n'est capable pour l'instant que d'installer les drivers graphiques des GPU.

- **mhwd-kernel** : est la commande pour gérer son ou plutôt ses kernels. C'est une des grandes possibilités que permet Manjaro c'est d'avoir des Kernels au pluriels. Des LTS en général et parfois aussi, des kernels intermédiaires afin de bénéficier soit de nouvelles fonctionnalités non incluses dans les LTS soit des corrections de bogues.



# MHWD




# MHWD-KERNEL
 
 
 Tout ce qui touche aux Kernels est un peu tabou sur la majorité des distributions Linux. D'ailleurs, on n'a souvent qu'un Kernel d'installé, celui-qui vient avec celle-ci.
 
Sous Manjaro, c'est totalement différent. On a le choix et d'ailleurs, il est fortement conseillé d'avoir deux kernels stables en plus du kernel que l'on utilise. Et C'est d'une facilité déconcertant. Le mieux est de voir avec quelques exemples la puissance et la simplicité de cet outil.

Listons d'abord nos Kernels installés sur notre système

	mhwd-kernel -li

Listons les Kernels qui sont disponibles à l'installation

	mhwd-kernel 
	
Installons le kernel 5.19 qui est le dernier lors de la création de ces lignes Sans supprimer celui-que l'on utilise ici le 


	sudo mhwd-kernel -i linux5.19
	
On peut faire tout autrement à la fois en installant le 5.19 et celui que l'on utilise avec la commande rmc

	sudo mhwd-kernel -i linux5.19 rmc

Desinstallons un kernel autre que celui que l'on utilise

	sudo mhwd-kernel -r linux4.19
	
Pour supprimer les headers du Kernel, on est obligé de passer par pacman

	sudo pacman -R linux4.19-headers
	
Pour supprimer les modules extras, on est obligé de passer par pacman 

	sudo pacman -R linux4.19-extramodules
	
Pour tout supprimer à la fois cad le kernel, les headers et les extras du module, on se sert de pacman

	sudo pacman -R linux4.19 linux4.19-headers linux4.19-extramodules

# Interface Graphique

Pour cela, il suffit d'aller dans Configuration System. Toutefois, le résultat graphique peut varier suivant l'environnement que vous utilisez. 
Dans KDE il est intégré à Configuration System tandis que sous Cinnamon il est disponible séparément. 

Pour KDE, mhwd puis mhwd-kernel

.. figure:: ./images/mhwd_kde.png

.. figure:: ./images/mhwd-kernel_kde.png


Pour Cinnamon

.. figure:: ./images/mhwd_cinnamon.png

.. figure:: ./images/mhwd-kernel_cinnamon.png
