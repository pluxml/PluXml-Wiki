Créer un thème
==============

Description des fichiers composant un thème
-------------------------------------------

Chaque thème est composé de plusieurs fichiers utiles au design et au bon fonctionnement de celui-ci.
Voici la liste des fichiers présents dans un thème (pour une meilleure compréhension, nous nous baserons sur le thème par défaut de PluXml).

Liste des fichiers situés à la racine de votre thème (par ordre alphabétique) :

* ``archives.php`` : gère les pages des archives
* ``article.php`` : gère les articles avec sidebar
* ``article-full-width.php`` : template qui gère les articles en pleine page (sans sidebar)
* ``categorie.php`` : gère l’affichage des articles en fonction d’une catégorie
* ``categorie-full-width.php`` : template qui gère les articles d’une catégorie en pleine page (sans
sidebar)
* ``commentaires.php`` : gère la partie commentaires des articles
* ``erreur.php`` : gère la page d’erreur
* ``footer.php`` : gère le pied de page de votre site
* ``header.php`` : gère l’entête de votre site
* ``home.php`` : gère la page d’accueil
* ``index.html`` : n’a aucune utilité pour le thème (présent par mesure de sécurité)
* ``infos.xml`` : regroupe les informations affichées sur la page Thèmes de l’administration
* ``preview.png`` : image miniature affichant l’aspect général du thème. Cette image est utilisée dans l’administration, menu Thèmes pour prévisualiser le thème
* ``sidebar.php`` : gère la barre latérale de votre site
* ``static.php`` : gère les pages statiques avec une sidebar
* ``static-full-width.php`` : template qui gère les pages statiques en pleine page (sans sidebar)
* ``tag.php`` : gère l’affichage des articles en fonction d’un tag

Votre thème contient également plusieurs dossiers importants :

* ``css/`` : contient les feuilles de style utilisées pour l’affichage du thème
    - Le thème par défaut s’appuie sur le framework css PluCSS développé par l’équipe de PluXml disponible à cette adresse : http://plucss.pluxml.org/. Il a pour objectif de faciliter et d’unifier l’utilisation du css pour homogénéiser le développement des
thèmes en se basant sur une même syntaxe de référence
    - Fichier ``plucss.css`` : framework css PluCSS
    - Fichier ``theme.css`` : contient la personnalisation propre au thème
* ``img/`` : contient les images utilisées dans votre thème (par exemple le favicon ou l’image présente en face des commentaires)
* ``lang/`` : contient les fichiers prenant en charge les différentes langues gérées par le thème (français, anglais, espagnol, ...)

Les modes d’affichage
---------------------

PluXml dispose de différents modes d’affichage, qui permettent d’afficher un contenu en tenant compte d’un contexte particulier. Par exemple, lorsque vous cliquez sur une catégorie dans le menu, vous entrez dans le mode d’affichage « Catégorie », qui va alors vous afficher les articles relatifs à la catégorie active.

Les différents modes d’affichage sont :

* home : gère la page d’accueil de votre site (dans votre thème : ``home.php``),
* categorie : gère l’affichage des articles par catégories (dans votre thème : ``categorie.php``),
* tag : gère l’affichage des articles par tags (dans votre thème : ``tags.php``),
* archive : gère l’affichage des articles par archives (dans votre thème ``archives.php``)
* articles : gère le contenu des articles (dans votre thème ``article.php``),
* statique : gère le contenu des pages statiques (dans votre thème ``static.php``),
* erreur : gère la page d’erreur de votre site (dans votre thème ``erreur.php``)

Les thèmes adaptés aux mobiles
------------------------------

Pour faciliter le développement de thème compatibilité avec les smartphones ou tablettes, nous vous conseillons d’utiliser le framework css PluCSS.

PluCSS est un Framework CSS dédié à PluXml. Cet outil est Full CSS (sans JavaScript), pensé pour le mobile (Mobile First), et s'adapte à toutes les résolutions d'écran (Responsive Design). Il est supporté par les principaux navigateurs modernes (Chrome, Firefox, IE9+, Opera, Safari) et valide W3C.

PluCSS est disponible à cette adresse : http://plucss.pluxml.org/
