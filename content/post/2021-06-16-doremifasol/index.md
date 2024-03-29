---
title: "doremifasol : un package R facilitant l'accès aux données Insee"
author: admin
date: 2021-06-22
description: "Une présentation du package doremifasol, sur lequel s'appuie la documentation utilitR"
draft: false
categories: ["doremifasol"]
tags: ["doremifasol","package"]
featured: true
image:
  caption: ""
  focal_point: ""
slug: doremifasol
---

## Qu'est-ce que doremifasol ?

Le _package_ `doremifasol` (_Données en R Mises à disposition par l’Insee et Facilement Sollicitables_) permet d'importer facilement dans `R` des données mises à disposition sur le site de l'Insee.

Il offre deux fonctionnalités principales :

* télécharger et importer dans `R` des fichiers disponibles sur insee.fr (Base Permanente des Équipements, Recensement de Population, Filosofi...) ;
* requêter l'[API](https://api.insee.fr/catalogue) Sirene et recupérer les résultats dans `R`.

L'objectif du _package_ est de rendre transparentes les différentes tâches à réaliser avant de pouvoir traiter les données : recherche sur le site, téléchargement, décompression, import dans `R`...

Le fonctionnement du _package_ et la liste des données disponibles sont consultables sur le [site dédié](https://inseefrlab.github.io/DoReMIFaSol).

Le code source est disponible sur [Github](https://github.com/InseeFrLab/DoReMIFaSol). Le _package_ s'installe dans `R` avec la commande suivante :

```r
remotes::install_github("inseefrlab/doremifasol")
```

## Exemple d'utilisation

On cherche des données récentes sur les naissances (source État Civil). On peut commencer par consulter la [liste des données téléchargeables](https://inseefrlab.github.io/DoReMIFaSol/articles/donnees_dispo.html).

En saisissant "naissances" dans la barre de recherche de cette page, on trouve plusieurs jeux de données. On choisit le plus récent à ce jour : "Données de naissances par commune, 2010-2019". Il a le nom court `"NAISSANCES_COM_1019"` (c'est ce nom qui servira pour les instructions suivantes).

Par acquit de conscience, on peut au préalable consulter la page de documentation de ces données sur le site de l'Insee :
```r
consulter("NAISSANCES_COM_1019")
```

Si cela correspond bien à ce que l'on souhaite, on importe directement les données dans `R` :
```r
naissances1019 <- telechargerDonnees("NAISSANCES_COM_1019")
```

Par défaut, les fichiers sont téléchargés dans un dossier temporaire. Il est possible de choisir un autre dossier (argument `telDir`). Celui-ci jouera le rôle de cache et évitera des re-téléchargements inutiles.

## Une source de données disponible sur insee.fr n'est pas dans le package ?

Vous pouvez la proposer en ouvrant une _[issue](https://github.com/InseeFrLab/DoReMIFaSol/issues/new/choose)_ sur le dépôt GitHub du package.

## Quel rapport avec `utilitR` ?

Afin de se rapprocher le plus possible des situations de travail rencontrées par les agents de l’Insee, la plupart des exemples de la documentation `utilitR` reposent sur des données produites et mises à disposition au grand public par l’Insee.

Le _package_ `doremifasol` a été utilisé pour récupérer des données dans `R` et créer un petit _package_ compagnon contenant les jeux de données utilisés dans les exemples de la documentation. C'est ce dernier _package_ (nommé `doremifasolData` et disponible [ici](https://inseefrlab.github.io/DoReMIFaSolData)) qui est utilisé pour disposer d'exemples reproductibles dans la documentation.
