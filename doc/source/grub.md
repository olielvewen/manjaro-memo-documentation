# GRUB chargeur de démarrage Linux

## Introduction

**GRand unified Bootloader (GRUB)** est un chargeur de démarrage et la version actuelle est GRUB 2, prenant en charge l'EUFI (ou UFi) et le mbr .
Ce chargeur de démarrage permet de démarrer un ou plusieurs système qu'ils soient Linux, BSD et même Windows.
On peut spécifier un certain nombre d'opérations comme paramétrer un temps d'affichage ou non, personnaliser le menu, avoir ou pas tous les noyaux disponibles afin d'en selectionner un, de charger un module spécifique par exemple le module intel pour utiliser le pilote libre intel pour les GPU Arc, etc.

```{Note}
 Il est préférable de faire une copie de sauvegarde avant de modifier le menu de GRUB
```

```{Warning}
 Il faut toujours regénérer Grub avec la commande  ``sudo update-grub`` sous peine de ne plus avoir de GRUB et d'être alors obligé de Chrooter pour le récupérer en passant dans un terminal la commande précédante.
```

Mais commençons par le début. Il faut d'abord connaître exactement ses partitions à l'aide de la commande:

    sudo fdisk -l

Pour lire le fichier grub:

    cat /etc/default/grub

On peut aussi utiliser cette commande:

    sudo grep "^[^#*/;]" /etc/default/grub

Pour sauvegarder le fichier grub:

    sudo cp /etc/default/grub /etc/default/grub


## Astuces


Voici une série d'astuces qui pourront vous êtres utiles.

- Faire apparaître les différents noyaux

Si vous utilisez KDE cet astuce peut vous être utile alors qu'il serait inutile si vous utilisez Cinnamon.

    1. On appuie sur la touche Esc après la disparition du splash
    2. On peut aussi éditer, modifier puis regenérer Grub afin d'éviter d'avoir à chaque fois appuyer sur Esc quand on veut selectionner un noyau différent.

Pour cela, avec votre Editeur/IDE préféré (kate, nano, geany,...), prenons Kate:

    kate /etc/default/grub

On édite ici le style du menu en tant qu'exemple

    GRUB_TIMEOUT_STYLE = menu

On met à jour grub avec:

    sudo update-grub

- Changer une valeur: ici le temps d'affichage de grub avant de basculer sur le noyau par defaut et donc de démarrer le système

On change la valeur de 5 par defaut à 10:

    GRUB_TIMEOUT = 10

puis on reconstruit grub car c'est un fichier de bas niveau avec:

    sudo grub-mkconfig -o /boot/grub/grub.cfg

Et on reboot pour voir si la modification a bien été prise en compte.

```{Note}
 Avec Nano, on descend en bas du fichier une fois les modifications faites puis Ctrl + X pour sortir du mode édition, la lettre <O> pour oui puis entré.
```

```{Note}
 En vrac pour l'instant: ``cat /boot/grub/grubenv`` et ``ls -lA /boot/grub/grubenv``
```