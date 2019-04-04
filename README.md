# Manacore Documentation

<p align="center"> 
<img src="images/logo_manacore.png">
</p>

## Objectif documentation

Le but de cette documentation est de donner une meilleure visibilité des différentes parties de Manacore pour les personnes y travaillant, ainsi la documentation est découpé en 4 parties principales (Backend, DevOps, Frontend, Mobile).
Chaque partie décrivent les technologies utilisées et leurs usages ainsi que des explication des architectures misent en place.
Le but est de donner à n’importe quel acteur sur le projet tous les éléments de compréhension pour pouvoir intervenir si nécessaire sur d’autres parties du projet de façon indépendante.

## Introduction à ManaCore

Manacore est un projet de gestion modulaire basée sur une architecture serveless à l’aide des technologies AWS.
Le projet est en partenariat avec l’association des paralysés de France de Talence, L’objectif de l’EIP est de pouvoir fournir à l’APF une solution fonctionnelle sur au moins trois services qui sont :

- **La gestion des lever /coucher**
- **La gestion des transports**
- **La gestion des repas**

Le projet se décline en un site web, et une application mobile utilisable respectivement par l’administration et les jeunes handicapés de l’APF.

Manacore est développé dans une optique d’architecture modulaire open source, le but est de pouvoir proposer un **Core** ou les différents utilisateurs pourrons avoir accès et ajouter uniquement les modules de gestion qui les intéressent et donc proposer une solution entièrement personnalisée à leur besoin.
Ils pourrons donc ainsi retrouver dans notre magasin en ligne tous nos modules disponibles et de choisir les modules adaptés à leur besoins, une fois leurs modules acheté, il leur suffira d’un simple clic pour les activer/ désactiver.
Le tout sera évidemment crée sous le signe de l’open source afin que la communauté puisse elle aussi créer des modules selon des besoins spécifiques et obtenir un pourcentage des ventes.

## Organisation

Le projet comporte 6 personnes répartis sur différentes parties comme ceci :

- Backend : Antoine, Valentin, Ludovic
- DevOps : Valentin, Robin
- Frontend : Thomas, Arthur, Ludovic
- Mobile (A venir) : Arthur, Robin

## Front-end

### Stack technique

- **VueJS Framework**
- **Pug**
- **Sass**

#### Introduction

Le Site web ManaCore est construit sous forme d'architecture modulaire à l'aide du Framework VueJS.
La logique de la partie Front de ManaCore est basé autour du Core permettant de gérer et de répertorier les modules pour les utilisateur.
On peut le representer comme ceci :

**INSERERSCHEMA**

**Core**: Le coeur logique du site, il liste et relie les modules entre eux.

**Store**: Les informations contenants differentes informations de l'utilisateur.

**Modules**: Les differentes fonctionnalités que l'utilisateur décide d'acheter/activer comme par exemple le module de calendrier.

##### Structure d'un Module

Les modules sont construits sous la forme de 4 composants differents:

- **Store** : en utilisant les fonctionnalités de VueX le store sert comme **state management pattern** et centralise les information d'utilisation concernant le module.

- **Router** : Centralise les fonctionnalités de Vue Router pour la navigation dans les differentes pages du component.

- **Pages** : C'est la vue entière de la page du module lui même.

- **Component** : Ce sont les differents component du module, ils doivent être appelé uniquement pour leur fonction, doivent etre réutilisables et modulaire.

Pour simplifier et uniformiser les modules nous vous conseillons d'utiliser le template de module et de suivre les instruction disponible sur cette page : https://gitlab.com/manacore-frontend/web-module-template

Afin de mettre en place une syntaxe plus légère le code des modules utilise régulièrement l'outil Pug pour la partie visuelle et Html.

## Back-end

Tout les services de ManaCore sont mis en place suivant une architecture serverless herbérgé avec les services AWS. Les services sont construits sous la forme de modules par le biais de différents services.

**INSERERSCHEMAARCHI**

**S3**: Services de stockage ou sont stockés différents éléments de ManaCore comme les différents modules et le site web.

**Lambda**: Container AWS utilisé pour run le code des différents modules.

**Cloudfront**: Service web utilisé pour la distribution de contenu web dynamiquement.

**Terraform**: Outil utilisé pour mettre en place l' infrastructure du projet

**INSERERSCHEMAREQUETEMODULE**

### Les modules

L'environnement de developpement d'module ManaCore se représente de cette manière:

<p align="center"> 
<img src="images/module_archi.png">
</p>

Le dossier Functions est l'environnement ou les différentes fonctionnalités du modules sont réparties. Dans le cas du module manager en exemple:

<p align="center"> 
<img src="images/module_functions.png">
</p>

Dans le cas du module manager ses differentes fonctions prennent la forme de dossiers composé de packages Go et du fichier de code qui serras transposé en Lanmbda AWS.(plus d'information ici https://aws.amazon.com/lambda/)

## DevOps
