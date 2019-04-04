# Manacore Documentation

<p align="center"> 
<img src="images/logo_manacore.png">
</p>

# Objectif documentation

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

##### Stack technique

- **VueJS Framework**
- **Pug**
- **Sass**

##### Introduction

Le Site web ManaCore est construit sous forme d'architecture modulaire à l'aide du Framework VueJS.
La logique du est basé autour du Core permettant de gérer et de répertorier les modules pour les utilisateur.
On peut le representer comme ceci :

Core: Le coeur logique du site, il liste et relie les modules entre eux.
Store: Les informations contenants differentes informations de l'utilisateur.
Modules: Les differentes fonctionnalités que l'utilisateur décide d'acheter/activer comme par exemple le module de calendrier.

##### Structure d'un Module

Les modules sont construits sous la forme de 4 composants differents:

- Store : en utilisant les fonctionnalités de VueX le store sert comme **state management pattern** et centralise les information d'utilisation concernant le module.

- Router : Centralise les fonctionnalités de Vue Router pour la navigation dans les differentes pages du component.

- Pages : C'est la vue entière de la page du module lui même.

- Component : Ce sont les differents component du module, ils doivent être appelé uniquement pour leur fonction, doivent etre réutilisables et modulaire.

Pour simplifier et uniformiser les modules nous vous conseillons d'utiliser le template de module et de suivre les instruction disponible sur cette page : https://gitlab.com/manacore-frontend/web-module-template

Afin de mettre en place une syntaxe plus légère le code des modules utilise régulièrement l'outil Pug pour la partie visuelle et Html.

## Back-end

## DevOps

_Because clean code is important!_

![xkcd](Documentation/images/code_quality_2.png)

Even though we think that freedom is ideal, we all have to follow some coding standards.

##### Functions

```python
def function(arg1, arg2, arg3, arg4):
        do some stuff
        if something:
            do some other stuff
        elif other thing:
            do other stuff
        else final case:
            do thing
    return value
```

The function above show some of the basics element of the function creation rules like, no more than 4 argument per functions, no **if forests**, no more than **80 collums**, no more than **25 lines per functions**. All this elements are more described in your handbook but help you code to be and more logical and easier to maintain.

## Unit testing

Unit testing is a very important part of your daily work.

```python
import unittest
from yourfile import your_function

class YourFunctionTest(unittest.TestCase):

    def test_empty_string(self):
        self.assertIs(your_function(""), True)

```

We provided you a basic implementation of the structure for your futures unit tests.

## Version control

For working in a clean environement and avoid merge conflict or branch conflict we recommand you to work with **git-flow**
You will see that your life will become much easier !
On each project you will work on you will find 3 branches, develop, release and master.
Here is an exemple on how to manage you work on those different branches in a team work using gitflow.

For example if you want to start a new feature on a project you will just to type:

```
git flow feature start FEATURENAME
```

![start_feature](Documentation/images/feature_start.png)

Will create a new branch based on the develop branch for you and switches to it.

For finishing the development of your feature you will juste have to use :

```
git flow feature FEATURENAME
```

![feature_finish](Documentation/images/feature_finish.png)

It will automatically merge your branch to develop, remove the feature branch for you and switch you back to the develop branch!
See? a lot more easier!

When your work is ready to be added to the release you can start a release process by using:

```
git flow release start RELEASE
```

![start_release](Documentation/images/start_release.png)

It will create a release branch created from the develop branch for preparing the merge on master.

If you want other developer to be able to push on this branch use the command :

```
git flow release publish RELEASE
```

This will make your release branch public for your team.

When your release branch is ready to be merge on master use

```
git flow release finish RELEASE
```

![finish_release](Documentation/images/feature_finish.png)

This simple command will perform several actions, merge the release branch into master, back-merges the release into develop and finally remove the release branch.

## Our Word

We poured a lot of time, effort and sweat into this tutorial and we will thank **gratefully** any developer that follows those working rules !

[handbook]: https://github.com/Ustarroz/SQA-Assignment-Ustarroz/Documentation/Handbook.docx
