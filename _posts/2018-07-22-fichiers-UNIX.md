---
layout: post
title:  "UNIX 1 : Les fichiers"
date:   2018-07-22 11h00
categories: UNIX
---

# Les fichiers

## Qu'est-ce qu'un fichier ?

Sous UNIX, tout est un fichier, que ce soit le fichier disque 'classique' ou le périphérique, les terminaux, les disques logiques et physiques ...
Ils sont de plusieurs types :
* **Réguliers**, les fichiers de programmes
* Les **Répertoires**, des fichiers servant d'intermédiaires de description des autres fichiers;
* Les **fichiers spéciaux**, en mode bloc, transitant par des caches systèmes, et en mode caractères transitant caractère par caractère.
* Les **tubes et les sockets**, moyen de communication entre les processus, multidiréctionnels pour les sockets.
* Les **liens symboliques**, renvoyant vers un autre fichier. 

## Comment sont enregistrés les fichiers ?

Chaque fichier est décrit par un *i-noeud* (ou noeud d'index) dans la table de partitions. Ce noeud contient plusieurs informations sur le fichier, dont son **type**, ses **propriétaires** (utilisateurs et groupes), sa **taille**, les **dates de ses dernières lectures/modifications**, les **blocs disques** et les **permissions des divers utilisateurs**.
Le nom n'est pas contenu dans l'_inode_ , ce qui permet par exemple qu'un fichier ai plusieurs noms.


### Permissions

L'i-noeud consacre 12 bits aux permissions d'un fichier :
Les 3 premiers servent à indiquer sous la forme read-write-execute les permissions de l'utilisateur propriétaire, 
Les trois suivants les permissions du groupe propriétaire,
Et les 3 d'après celles du reste des utilisateurs.
Les 3 derniers sont :
* Le set-uid, qui permet d'accéder au fichier en utilisant l'identité du propriétaire
* Le set-gid, qui permet d'accéder au fichier en utilisant l'identité du groupe propriétaire
* et le sticky-bit, dont le but était à l'origine d'indiquer si il fallait conserver le fichier en mémoire swap.

## Quelles commandes pour y accéder ?

### Lecture
* `pwd` affiche une référence absolue du répertoire de travail du shell
* et `cd` permet d'en changer
* `ls` permet de lister le contenu d'un répertoire, de travail par défaut.
* `cat` affiche le contenu brut d'un fichier donné
* `od` permet de visualiser le contenu d'un fichier dans divers formats (hexadécimal, décimal, octal...)

### Écriture
* `chmod` permet de changer les permissions d'un fichier
* `chown` et `chgrp` permettent d'en changer le propriétaire et le groupe propriétaire
* `cp` fait une copie d'un fichier

### Actions sur le lien
* `ln` crée un nouveau lien vers un fichier existant
* `mv` et `rm` servent respectivement à renommer et supprimer un lien
