Fonctions plxShow
=================

Toutes les fonctions offertes par PluXml pour personnaliser votre thème.

La classe **plxShow** est responsable de l'affichage. Elle permet donc de modifier cet affichage, ce qui se fait grâce à des fonctions prédéfinies.

Vous trouverez dans le menu de droite ces différentes fonctions qui vous permettront de modifier l'affichage par défaut de PluXml.

**Usage**

Le principe général pour utiliser la classe **plxShow** est le suivant :

.. code:: php

    <?php $plxShow->nomFonction() ?>

Certaines fonctions possèdent des variables prédéfinies, l'usage général devient ainsi :

.. code:: php

    <?php $plxShow->nomFonction('$variable') ?>


archList
--------

**Usage**

.. code:: php

    <?php $plxShow->archList('$format') ?>

**Détails des paramètres**

* **$format** (string) (optionnel) : format du texte pour l'affichage ; valeurs possibles :
    * archives_id : affiche l'ID de l'archive
    * archives_status : affiche le status de l'archive (active / noactive)
    * archives_nbart : affiche le nombre d'articles
    * archives_url : affiche l'URL de l'archive
    * archives_name : affiche le nom de l'archive (mois + année)
    * archives_month : affiche le mois de l'archive
    * archives_year : affiche l'année de l'archive
    * valeur libre : caractère libre

**Exemples**

.. code:: php

    <?php $plxShow->archList() ?>

.. code:: php

    <?php $plxShow->archList('<li id="#archives_id">
    <a class="#archives_status" href="#archives_url" title="#archives_name">
    #archives_name (#archives_nbart)</a></li>') ?>

artAuthorEmail
--------------

**Usage**

.. code:: php

    <?php $plxShow->artAuthorEmail() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->artAuthorEmail() ?>

artAuthorInfos
--------------

**Usage**

.. code:: php

    <?php $plxShow->artAuthorInfos('$format') ?>

**Détails des paramètres**

* **$format** (string) (optionnel) : permet de préciser une mise en page. Formatage par défaut : `<div class="author-infos"></div>`. Valeur disponible :
    *  art_authorinfos : permet d'afficher les informations sur l'auteur  (utile quand on personnalise la mise en page)

**Exemples**

.. code:: php

    <?php $plxShow->artAuthorInfos() ?>

.. code:: php

    <?php $plxShow->artAuthorInfos('<div>#art_authorinfos</div>') ?>

artAuthor
---------

**Usage**

.. code:: php

    <?php $plxShow->artAuthor($echo) ?>

**Détails des paramètres**

* **$echo** (boolean) (optionnel) : valeurs possibles : true / false. Par défaut la valeur est à true. Si la valeur est à false, alors le nom de l'auteur ne sera pas affiché

**Exemples**

.. code:: php

    <?php $plxShow->artAuthor() ?>

.. code:: php

    <?php $plxShow->artAuthor(true) ?>

.. code:: php

    <?php $plxShow->artAuthor(false) ?>

artCatId
--------

**Usage**

.. code:: php

    <?php $plxShow->artCatId() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->artCatId() ?>

**Exemple avancé**

.. code:: php

    <?php
        $var = $plxShow->artCatId();
        echo $var;
    ?>

artCat
------

**Usage**

.. code:: php

    <?php $plxShow->artCat('$separator') ?>

**Détails des paramètres**

* **$separator** (string) (optionnel) : caractère de séparation entre les catégories affichées ; valeur par défaut : ','

**Exemple**

.. code:: php

    <?php $plxShow->artCat('|') ?>

artChapo
--------

**Usage**

.. code:: php

    <?php $plxShow->artChapo('$format',$content) ?>

**Détails des paramètres**

* **$format** (string) (optionnel) : format d'affichage du lien pour lire la suite de l'article ; valeur par défaut : #art_title ; valeurs possibles :
    *  art_title : affiche le titre de l'article dans le lien "pour lire la suite" de l'article
    *  valeur libre : chaîne de caractère de son choix
* **$content** (boolean) (optionnel) : affichage oui ou non le contenu de l'article si le chapô est vide ; valeur par défaut : true ; valeurs possibles : true / false ; *Note* : si la valeur est à false, alors $format ne sera pas affiché.

**Exemples**

.. code:: php

    <?php $plxShow->artChapo('#art_title',true) ?>

.. code:: php

    <?php $plxShow->artChapo('Continuer la lecture',true) ?>

artContent
----------

**Usage**

.. code:: php

    <?php $plxShow->artContent($chapo) ?>

**Détails des paramètres**

* **$chapo** (boolean) (requis) : affiche oui ou non le chapô ; valeurs possible : true / false ; valeur par défaut : true

**Exemples**

.. code:: php

    <?php $plxShow->artContent() ?>

.. code:: php

    <?php $plxShow->artContent(true) ?>

.. code:: php

    <?php $plxShow->artContent(false) ?>

artDate
-------

**Usage**

.. code:: php

    <?php $plxShow->artDate('$format') ?>

**Détails des paramètres**

* **$format** (string) (optionnel) : format de la date ; valeurs par défaut : '#day #num_day #month #num_year(4)' ; valeurs possibles :
    *  minute : affiche les minutes
    *  hour : affiche l'heure de publication
    *  day : affiche le jour (au format texte : lundi, mardi, etc...)
    *  month : affiche le mois (au format texte : janvier, février, mars, etc...)
    *  num_day : affiche le numéro du jour du mois (1, 15, ..., 31,)
    *  num_month : affiche le numéro du mois (1, 2, 5, ..., 12)
    *  num_year(4) : affiche l'année sur 4 chiffres (ex: 2012)
    *  num_year(2) : affiche l'année sur 2 chiffres (ex: 12)
    *  valeur libre : chaîne de caractère de son choix

**Exemples**

.. code:: php

    <?php $plxShow->artDate() ?>

.. code:: php

    <?php $plxShow->artDate('#num_day #month #num_year(4)') ?>

**Exemples avancés**

Formatage avancé avec des caractères libres :

.. code:: php

    <?php $plxShow->artDate('#hour:#minute') ?>

.. code:: php

    <?php $plxShow->artDate('#num_day/#num_month/#num_year(4)') ?>

artFeed
-------

**Usage**

.. code:: php

    <?php $plxShow->artFeed('$type',$categorie,'$format') ?>

**Détails des paramètres**

* **$type** (obsolete)
* **$categorie** (integer) (optionnel) : identifiant (ID sans les 0) d'une catégorie
* **$format** (string) (optionnel) : format du lien ; valeurs possibles :
    *  feedUrl : url du flux RSS
    *  feedName : nom du flux RSS

**Exemples**

Flux RSS des articles de tout le site :

.. code:: php

    <?php $plxShow->artFeed() ?>

Flux RSS des articles de la catégorie 1 :

.. code:: php

    <?php $plxShow->artFeed('',1, '<a href="#feedUrl" title="#feedTitle">#feedName</a>') ?>

*Note* : les guillemets simples vides ('') sont obligatoires quand on précise une catégorie, à cause du paramètre obsolete **$type**

artId
-----

**Usage**

.. code:: php

    <?php $plxShow->artId() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->artId() ?>

**Exemple avancé**

.. code:: php

    <?php
        $var = $plxShow->artId();
        echo $var;
    ?>

artNbCom
--------

**Usage**

.. code:: php

    <?php $plxShow->artNbCom('$f1','$f2','$f3') ?>

**Détails des paramètres**

* **$f1** (string) (optionnel) : format d'affichage si nombre de commentaire = 0 ; variable possible : #nb pour afficher le nombre de commentaire ; valeur par défaut 'aucun commentaire'
* **$f2** (string) (optionnel) : format d'affichage si nombre de commentaire = 1 ; variable possible : #nb pour afficher le nombre de commentaire ; valeur par défaut '#nb commentaire'
* **$f2** (string) (optionnel) : format d'affichage si nombre de commentaire > 1 ; variable possible : #nb pour afficher le nombre de commentaires ; valeur par défaut '#nb commentaires'

**Exemples**

.. code:: php

    <?php $plxShow->artNbCom() ?>

.. code:: php

    <?php $plxShow->artNbCom('#nb commentaire','#nb commentaire','#nb commentaires') ?>

.. code:: php

    <?php $plxShow->artNbCom('#nb','#nb','#nb') ?>

artTags
-------

**Usage**

.. code:: php

    <?php $plxShow->artTags('$format','$separor') ?>

**Détails des paramètres**

* **$format** (string) (optionnel) : format du texte pour chaque tag ; valeurs par défauts : `<a class="#tag_status" href="#tag_url" title="#tag_name">#tag_name</a>` ; valeurs possibles :
    *  tag_status : permet d'ajouter 'class="noactive"' ou 'class="active"' à l'attribut HTML 'a' (permet de définir un style CSS quand un tag est actif, c'est à dire consulté)
    *  tag_url : l'URL du tag
    *  tag_name : le nom du tag
* **$separator** (string) (optionnel) : caractère de séparation entre les tags affichées ; valeur par défaut : ','

**Exemples**

.. code:: php

    <?php $plxShow->artTags('<a class="#tag_status" href="#tag_url" title="#tag_name">#tag_name</a>',',') ?>

.. code:: php

    <?php $plxShow->artTags('<a href="#tag_url" title="#tag_name">#tag_name</a>',' |') ?>

**Exemple avancé**

.. code:: php

    <ul>
        <?php $plxShow->artTags('<li><a href="#tag_url" title="#tag_name">#tag_name</a></li>','') ?>
    </ul>

artTitle
--------

**Usage**

.. code:: php

    <?php $plxShow->artTitle('$type') ?>

**Détails des paramètres**

* **$type** (string) (optionnel) : valeur possible : 'link'. Affiche le titre de l'article sous forme d'un lien cliquable

**Exemples**

.. code:: php

    <?php $plxShow->artTitle() ?>

.. code:: php

    <?php $plxShow->artTitle('link') ?>

artThumbnail
------------

**Usage**

.. code:: php

    <?php $plxShow->artThumbnail('$format', $echo); ?>

**Détails des paramètres**

* **$format** (string) (optionnel) : format du texte pour chaque tag ; valeurs par défauts : `<a href="#img_url"><img class="art_thumbnail" src="#img_thumb_url" alt="#img_alt" title="#img_title" /></a>` ; valeurs possibles :
    *  img_url : l'URL de l'image d'accroche
    *  img_thumb_url : l'URL de la miniature de l'image d'accroche
    *  img_title : Titre de l'image d'accroche
    *  img_alt : Texte alternatif d'affichage de l'image d'accroche
* **$echo** (boolean) (optionnel) : valeurs possibles : true / false. Par défaut la valeur est à true. Si la valeur est à false, alors l'image ne sera pas affiché
* **$article** (boolean) (optionnel) : valeurs possibles : true / false. Par défait la valeur est false. Si la valeur est true, alors au clic sur l'image PluXml redirige vers l'article et non vers l'image.

**Exemples**

.. code:: php

    <?php $plxShow->artThumbnail() ?>

.. code:: php

    <?php $plxShow->artThumbnail('<a href="#img_url">
    <img class="art_thumbnail" src="#img_thumb_url" alt="#img_alt" title="#img_title" /></a>', true) ?>

artUrl
------

**Usage**

.. code:: php

    <?php $plxShow->artUrl() ?>

**Détails des paramètres**

* **$type** (deprecated) : lien relatif ou absolu

**Exemple**

.. code:: php

    <?php $plxShow->artUrl() ?>

**Exemple avancé**

Partager facilement un article sur les réseaux sociaux :

.. code:: html

    <a href="http://www.facebook.com/sharer.php?u=<?php $plxShow->artUrl() ?>">Partager sur Facebook</a>

callHook
--------

**Usage**

.. code:: php

    <?php $plxShow->callHook('$hookName','$parms') ?>

**Détails des paramètres**

* **$hookName** (string) (requis) : nom du hook
* **$parms** (string) (requis) : paramètre ou liste de paramètres sous forme de array

**Exemple**

Sans return, passage d'un paramètre :

.. code:: php

    <?php eval($plxShow->callHook('MyPluginFunction', 'AZERTY')); ?>

Avec return, passage de 2 paramètres à faire sous forme de tableau :

.. code:: php

    <?php $b = $plxShow->callHook('MyPluginFunction', array('AZERTY', 'QWERTY')); ?>

capchaQ
-------

**Usage**

.. code:: php

    <?php $plxShow->capchaQ() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->capchaQ() ?>

capchaR
-------

**Usage**

.. code:: php

    <?php $plxShow->capchaR() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->capchaR() ?>

catDescription
--------------

**Usage**

.. code:: php

    <?php $plxShow->catDescription() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->catDescription() ?>

catId
-----

**Usage**

.. code:: php

    <?php $plxShow->catId() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->catId() ?>

**Exemple avancé**

.. code:: php

    <?php
        $var = $plxShow->catId();
        echo $var;
    ?>

catList
-------

**Usage**

.. code:: php

    <?php $plxShow->catList('$extra','$format','include','exclude') ?>

**Détails des paramètres**

* **$extra** (string) (requis) : nom du lien vers la page d'accueil ; si on ne veut pas de lien vers la page d'accueil, mettre des guillemets simples vides ('')
* **$format** (string) (requis) : format du texte pour chaque catégorie ; valeurs possibles :
    *  cat_id : ID de la catégorie
    *  cat_status : statut de la catégorie (active, noactive)
    *  cat_url : url de la catégorie
    *  cat_name : nom de la catégorie
    *  art_nb : nombre d'articles dans cette catégorie
* **$include** (integer) (optionnel) : liste des catégories à afficher séparées par le caractère '|'
* **$exclude** (integer) (optionnel) : liste des catégories à ne pas afficher séparées par le caractère '|' ; si renseigné, $include doit contenir des guillements simples vides

**Exemples**

.. code:: php

    <?php $plxShow->catList('Accueil','<li><a href="#cat_url" title="#cat_name">#cat_name</a></li>'); ?>

.. code:: php

    <?php $plxShow->catList('','<li id="#cat_id" class="#cat_status">
    <a href="#cat_url" title="#cat_name">#cat_name</a> (#art_nb)</li>'); ?>

*Note* : on notera les guillemets simples vides '' obligatoires quand on ne veut pas de lien vers la page d'accueil.

L'exemple suivant n'affichera que la catégorie numéro 1 :

.. code:: php

    <?php $plxShow->catList('','<li><a href="#cat_url" title="#cat_name">#cat_name</a></li>',1); ?>

L'exemple suivant affichera toutes les catégories **sauf** la catégorie numéro 2 :

.. code:: php

    <?php $plxShow->catList('','<li><a href="#cat_url" title="#cat_name">#cat_name</a></li>','',2); ?>

**Exemple avancé**

Il est possible de passer une variable dans les paramètres :

.. code:: php

    <?php
        $catInclude = 3;
        $plxShow->catList('','<li><a href="#cat_url" title="#cat_name">#cat_name</a></li>',$catInclude);
    ?>

.. code:: php

    <?php
        $homeTitle = 'Accueil';
        $plxShow->catList($homeTitle,'<li><a href="#cat_url" title="#cat_name">#cat_name</a></li>');
    ?>

Voyons à présent un exemple avec la fonction mode :

.. code:: php

    <?php
        $mode = $plxShow->mode();
        if ($mode == 'home') {
            $homeTitle = "Accueil";
        }
        else{
            $homeTitle = "retour à l'Accueil";
        }
        $plxShow->catList($homeTitle,'<li><a href="#cat_url" title="#cat_name">#cat_name</a></li>');
    ?>

catName
-------

**Usage**

.. code:: php

    <?php $plxShow->catName('$type') ?>

**Détails des paramètres**

* **$type** (string) (optionnel) : valeur possible : 'link'. Affiche le nom de la catégorie sous forme d'un lien cliquable

**Exemples**

.. code:: php

    <?php $plxShow->catName() ?>

.. code:: php

    <?php $plxShow->catName('link') ?>

catThumbnail
------------

**Usage**

.. code:: php

    <?php $plxShow->catThumbnail('$format', $echo); ?>

**Détails des paramètres**

* **$format** (string) (optionnel) : format du texte pour chaque tag ; valeurs possibles :
    *  img_url : l'URL de l'image d'accroche
    *  img_thumb_url : l'URL de la miniature de l'image d'accroche
    *  img_title : Titre de l'image d'accroche
    *  img_alt : Texte alternatif d'affichage de l'image d'accroche
* **$echo** (boolean) (optionnel) : valeurs possibles : true / false. Par défaut la valeur est à true. Si la valeur est à false, alors l'image ne sera pas affichée

**Exemples**

.. code:: php

    <?php $plxShow->catThumbnail() ?>

.. code:: php

    <?php $plxShow->catThumbnail('<a href="#img_url">
    <img class="cat_thumbnail" src="#img_thumb_url" alt="#img_alt" title="#img_title" /></a>', true) ?>

catUrl
------

**Usage**

.. code:: php

    <?php $plxShow->catUrl($id) ?>

**Détails des paramètres**

* **$id** (integer) (requis) : id de la categorie sous la forme numérique ou formatée (ex: 1 ou 001)

**Exemple**

.. code:: php

    <?php $plxShow->catUrl(1) ?>

**Exemple avancé**

.. code:: php

    <?php
        $var = $plxShow->catUrl(1);
        echo $var;
    ?>

Cet exemple affichera *http://example.org/categorie1/nom-de-ma-categorie*

charset
-------

**Usage**

.. code:: php

    <?php $plxShow->charset('$casse'); ?>

**Détails des paramètres**

* **$casse** (string) (optionnel) : la $casse est soit 'min' soit 'maj'. Par défaut 'min'.

**Exemples**

.. code:: php

    <?php $plxShow->charset(); ?>

Affichera par exemple :

.. code:: none

    utf-8

Autre exemple

.. code:: php

    <?php $plxShow->charset('maj'); ?>

Affichera par exemple :

.. code:: none

    UTF-8

**Exemple avancé**

.. code:: html

    <meta http-equiv="Content-Type" content="text/html; charset=<?php $plxShow->charset(); ?>" />

chrono
------

**Usage**

.. code:: php

    <?php $plxShow->chrono() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: html

    <p>Page générée en <?php $plxShow->chrono() ?></p>

comAuthor
---------

**Usage**

.. code:: php

    <?php $plxShow->comAuthor('$type') ?>

**Détails des paramètres**

* **$type** (string) (optionnel) : affiche le nom de l'auteur sous forme de lien vers son site ; valeur possible : 'link' ;

**Exemples**

.. code:: php

    <?php $plxShow->comAuthor() ?>

.. code:: php

    <?php $plxShow->comAuthor('link') ?>

comContent
----------

**Usage**

.. code:: php

    <?php $plxShow->comContent() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->comContent() ?>

comDate
-------

**Usage**

.. code:: php

    <?php $plxShow->comDate('$format') ?>

**Détails des paramètres**

* **$format** (string) (optionnel) : format du texte de la date ; valeurs possibles :
    *  minute : affiche les minutes
    *  hour : affiche l'heure
    *  day : affiche le nom du jour (lundi, mardi, etc...)
    *  month : affiche le nom du mois (janvier, février, etc...)
    *  num_day : affiche le numéro du jour (01, 15, 31)
    *  num_month : affiche le numéro du mois (01, 06, 12)
    *  num_year(2) : affiche l'année au format court (ex: 12)
    *  num_year(4) : affiche l'année au format long (ex: 2012)
    *  valeur libre : un caractère au choix

**Exemples**

.. code:: php

    <?php $plxShow->comDate('#day #num_day #month #num_year(4)') ?>

.. code:: php

    <?php $plxShow->comDate('#num_day/num_#month/#num_year(4)') ?>

comFeed
-------

**Usage**

.. code:: php

    <?php $plxShow->comFeed('$type',$article,'$format') ?>

**Détails des paramètres**

* **$type** (string) (OBSOLETE - requis, vide) : type de flux
* **$article** (integer) (optionnel) : identifiant (sans les 0) d'un article
* **$format** (string) (optionnel) : format du lien ; valeurs possibles :
    *  feedUrl : url du flux RSS
    *  feedName : nom du flux RSS

**Exemple**

.. code:: php

    <?php $plxShow->comFeed() ?>

.. code:: php

    <?php $plxShow->comFeed('',3,'<a href="#feedUrl" title="#feedTitle">#feedName</a>') ?>

*Note* : les guillemets simples sont obligatoires quand on précise l'ID de l'article en raison du paramètre $type obsolète

comGet

**Usage**

.. code:: php

    <?php $plxShow->comGet($key,'$defaut') ?>

*Note* : manque de précision

**Détails des paramètres**

* **$key** (string) (requis) : clé du tableau GET
* **$defaut** (string) (requis) : valeur par défaut si variable vide

comId
-----

**Usage**

.. code:: php

    <?php $plxShow->comId() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->comId() ?>

comMessage
----------

**Usage**

.. code:: php

    <?php $plxShow->comMessage() ?>

*Note* : manque de précision

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->comMessage() ?>

comType
-------

**Usage**

.. code:: php

    <?php $plxShow->comType() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->comType() ?>

**Exemple avancé**

Cette fonction est utile pour un habillage CSS différent quand le commentaire est écrit par l'admin du site :

.. code:: php

    <div class="<?php $plxShow->comType() ?>">ON AFFICHE ICI LE COMMENTAIRE</div>

comUrl
------

**Usage**

.. code:: php

    <?php $plxShow->comUrl() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->comUrl() ?>

defaultLang
-----------

**Usage**

.. code:: php

    <?php $plxShow->defaultLang($echo) ?>

**Détails des paramètres**

* **$echo** (boolean) (optionnel) : si TRUE, affichage à l'écran

**Exemple**

.. code:: php

    <?php $plxShow->defaultLang(true) ?>

erreurMessage
-------------

**Usage**

.. code:: php

    <?php $plxShow->erreurMessage() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->erreurMessage() ?>

getLang
-------

**Usage**

.. code:: php

    <?php $plxShow->getLang('$key') ?>

**Détails des paramètres**

* **$key** (string) (requis) : clé de traduction à afficher

**Exemple**

.. code:: php

    <?php $plxShow->getLang('HOME') ?>

**Liste des termes**

Vous pouvez trouver la liste dans termes dans les fichiers du répertoire */themes/defaut/lang/*.

Voici la liste des termes :

* header.php :
    *  HOME
    *  GOTO_CONTENT
    *  GOTO_MENU
    *  COMMENTS_RSS_FEEDS
    *  COMMENTS
    *  ARTICLES_RSS_FEEDS
    *  ARTICLES

* sidebar.php :
    *  CATEGORIES
    *  LAST_ARTICLES
    *  LAST_COMMENTS
    *  ARCHIVES

* footer.php :
    *  POWERED_BY
    *  PLUXML_DESCRIPTION
    *  IN
    *  ADMINISTRATION
    *  GOTO_TOP
    *  TOP

* erreur.php :
    *  ERROR
    *  BACKTO_HOME

* common :
    *  WRITTEN_BY
    *  CLASSIFIED_IN
    *  TAGS

* commentaires.php :
    *  SAID
    *  WRITE_A_COMMENT
    *  NAME
    *  WEBSITE
    *  EMAIL
    *  COMMENT
    *  CLEAR
    *  SEND
    *  COMMENTS_CLOSED
    *  ANTISPAM_WARNING

get
---

**Usage**

.. code:: php

    <?php $plxShow->get() ?>

*Note* : manque de précision

**Détail des paramètres**

aucun

httpEncoding
------------

**Usage**

.. code:: php

    <?php $plxShow->httpEncoding() ?>

**Détail des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->httpEncoding() ?>

Si la compression Gzip est activée dans les paramètres avancés de PluXml, alors cette fonction affichera :

    Compression GZIP activée

lang
----

**Usage**

.. code:: php

    <?php $plxShow->lang('$key') ?>

**Détails des paramètres**

* **$key** (string) (requis) : texte traduit par PluXml

**Exemple**

.. code:: php

    <?php $plxShow->lang('CATEGORIES') ?>

**Liste des termes**

Vous pouvez trouver la liste dans termes dans les fichiers du répertoire **/themes/defaut/lang/**.

Voici la liste des termes :

* header.php :
    *  HOME
    *  GOTO_CONTENT
    *  GOTO_MENU
    *  COMMENTS_RSS_FEEDS
    *  COMMENTS
    *  ARTICLES_RSS_FEEDS
    *  ARTICLES

* sidebar.php :
    *  CATEGORIES
    *  LAST_ARTICLES
    *  LAST_COMMENTS
    *  ARCHIVES

* footer.php :
    *  POWERED_BY
    *  PLUXML_DESCRIPTION
    *  IN
    *  ADMINISTRATION
    *  GOTO_TOP
    *  TOP

* erreur.php :
    *  ERROR
    *  BACKTO_HOME

* common :
    *  WRITTEN_BY
    *  CLASSIFIED_IN
    *  TAGS

* commentaires.php :
    *  SAID
    *  WRITE_A_COMMENT
    *  NAME
    *  WEBSITE
    *  EMAIL
    *  COMMENT
    *  CLEAR
    *  SEND
    *  COMMENTS_CLOSED
    *  ANTISPAM_WARNING

lastArtList
-----------

**Usage**

.. code:: php

    <?php $plxShow->lastArtList('$format',$max,$cat_id,'$ending',$sort) ?>

**Détails des paramètres**

* **$format** (string) (optionnel) : format du texte pour chaque article ; valeurs possibles :
    *  art_id : affiche l'ID de l'article
    *  art_url : affiche l'URL de l'article
    *  art_status : affiche le status de l'article (active / noactive)
    *  art_author : affiche l'auteur de l'article
    *  art_title : affiche le titre de l'article
    *  art_chapo : affiche le chapô de l'article
    *  art_content : affiche un extrait du contenu de l'article
    *  art_content(num) : affiche un extrait du contenu de l'article en précisant le nom de caractère affichés
    *  art_date : affiche la date de publication de l'article au format court (jj/mm/aaaa)
    *  art_hour : affiche l'heure de publication de l'article au format court (hh:mm)
    *  cat_list : affiche les catégories auxquelles appartient l'article sous forme d'un lien
    *  art_nbcoms : affiche le nombre de commentaires pour chaque article
* **$max** (integer) (optionnel) : nombre d'article à afficher ; valeur par defaut : 5
* **$cat_id** (integer) (optionnel) : limiter l'affiche des articles à une catégorie précise
* **$ending** (string) (optionnel) : texte à ajouter en fin de ligne ; *Note* : ne semble pas fonctionner
* **$sort** (string) (optionnel) : ordre de trie. Valeur possible sort|rsort|alpha|random

**Exemple**

.. code:: php

    <?php $plxShow->lastArtList('<li><a href="#art_url" title="#art_title">#art_title</a></li>',3) ?>

Limiter l'affichage aux 5 derniers articles de la catégorie 1 :

.. code:: php

    <?php $plxShow->lastArtList('<li><a href="#art_url" title="#art_title">#art_title</a></li>',5,1) ?>

lastComList
-----------

**Usage**

.. code:: php

    <?php $plxShow->lastComList('$format',$max,$art_id,$cat_ids) ?>

**Détails des paramètres**

* **$format** (string) (optionnel) : format du texte pour chaque commentaire ; valeurs possibles :
    *  com_id : affiche l'ID du commentaire
    *  com_url : affiche l'URL du commentaire
    *  com_author : affiche l'auteur du commentaire
    *  com_content(num) : affiche les N (num) premiers caractères du commentaire
    *  com_content : affiche le commentaire dans son intégralité
    *  com_date : affiche la date du commentaire
    *  com_hour : affiche l'heure de commentaire
    *  valeur libre : caractère libre
* **$max** (integer) (optionnel) : nombre de commentaires maximum à afficher ; valeur par défaut : 5
* **$art_id** (integer) (optionnel) : restreindre l'affichage des derniers commentaires à un article précis via son ID (ex: 24, 3)
* **$cat_ids** (integer) (optionnel) : restreindre l'affichage des derniers commentaires à certaines catégories via leur ID (ex: 1|2 ; voir exemples)

**Exemples**

Affichage basique :

.. code:: php

    <?php $plxShow->lastComList(
      '<li><a href="#com_url">#com_author a dit :</a><p>#com_content(50)</p></li>') ?>

Afficher seulement les 3 derniers commentaires :

.. code:: php

    <?php $plxShow->lastComList(
      '<li><a href="#com_url">#com_author a dit :</a><p>#com_content(50)</p></li>',3) ?>

Afficher seulement les 3 derniers commentaires de l'article ayant l'ID 9 :

.. code:: php

    <?php $plxShow->lastComList(
      '<li><a href="#com_url">#com_author a dit :</a><p>#com_content(50)</p></li>',3,9) ?>

Afficher seulement les 3 derniers commentaires de la catégorie 6 :

.. code:: php

    <?php $plxShow->lastComList(
      '<li><a href="#com_url">#com_author a dit :</a><p>#com_content(50)</p></li>',3,'',6) ?>

*Note* : notez les guillements simples '' à la place de **$art_id**

Afficher seulement les 3 derniers commentaires des catégories 6 et 8 :

.. code:: php

    <?php $plxShow->lastComList(
      '<li><a href="#com_url">#com_author a dit :</a><p>#com_content(50)</p></li>',3,'',6|8) ?>

mainTitle
---------

**Usage**

.. code:: php

    <?php $plxShow->mainTitle('$type') ?>

**Détails des paramètres**

* **$type** (string) (optionnel) : type d'affichage en format texte ou sous forme de lien ; valeur possible : link

**Exemples**

.. code:: php

    <?php $plxShow->mainTitle() ?>

.. code:: php

    <?php $plxShow->mainTitle('link') ?>

**Exemple avancé**

.. code:: html

    <div id="header"><h1><?php $plxShow->mainTitle('link') ?></h1></div>

*Note*

* cette fonction définie le contenu et la cible du lien. Pour personnaliser le contenu du lien, voir la [fontion racine|plxShow-racine]

meta
----

**Usage**

.. code:: php

    <?php $plxShow->meta('$meta') ?>

**Détails des paramètres**

* **$meta** (string) (requis) : nom du meta à afficher ; les différentes valeurs possibles sont : description, keywords, author

**Exemples**

.. code:: php

    <?php $plxShow->meta('description') ?>

.. code:: php

    <?php $plxShow->meta('keywords') ?>

.. code:: php

    <?php $plxShow->meta('author') ?>

*Note*

* Cette fonction sert principalement à remplir automatiquement les champs "meta" de la balise `<head></head>`
* Lors de la rédaction d'un article, vous pouvez indiquer le contenu des balises "description" et "keywords"

mode
----

**Usage**

.. code:: php

    <?php $plxShow->mode() ?>

**Détail des paramètres**

aucun

**Exemple**

.. code:: php

    <?php
        $var = $plxShow->mode();
        echo $var;
    ?>

Affichera soit home, article, categorie, static, archives ou tags.

**Exemple avancé**

.. code:: php

    <?php
        $var = $plxShow->mode();
        if ($var == 'home') {
            echo "mode HOME";
        }
        else{
            echo "mode NON HOME";
        }
    ?>

nbAllArt
--------

**Usage**

.. code:: php

    <?php $plxShow->nbAllArt() ?>

**Détails des paramètres**

* **$f1** (string) (optionnel) : format d'affichage si nombre d'article = 0 ; variable possible : `#nb` pour afficher le nombre d'article ; valeur par défaut 'aucun article'
* **$f2** (string) (optionnel) : format d'affichage si nombre d'article = 1 ; variable possible : `#nb` pour afficher le nombre d'article ; valeur par défaut '#nb article'
* **$f2** (string) (optionnel) : format d'affichage si nombre d'article > 1 ; variable possible : `#nb` pour afficher le nombre d'articles ; valeur par défaut '#nb articles'

**Exemples**

.. code:: php

    <?php $plxShow->nbAllArt() ?>

.. code:: php

    <?php $plxShow->nbAllArt('aucun article','#nb article publié','#nb articles au total') ?>

nbAllCom
--------

**Usage**

.. code:: php

    <?php $plxShow->nbAllCom('$f1','$f2','$f3') ?>

**Détails des paramètres**

* **$f1** (string) (optionnel) : format d'affichage si nombre de commentaire = 0 ; valeur possible : `#nb` pour afficher le nombre de commentaire
* **$f2** (string) (optionnel) : format d'affichage si nombre de commentaire = 1 ; valeur possible : `#nb` pour afficher le nombre de commentaire
* **$f3** (string) (optionnel) : format d'affichage si nombre de commentaire > 0 ; valeur possible : `#nb` pour afficher le nombre de commentaire

**Exemples**

.. code:: php

    <?php $plxShow->nbAllCom() ?>

.. code:: php

    <?php $plxShow->nbAllCom('Aucun commentaire', '#nb commentaire', '#nb commentaires au total') ?>

pageBlog
--------

**Usage**

.. code:: php

    <?php $plxShow->pageBlog('$format') ?>

**Détails des paramètres**

* **$format** (string) (optionnel) : format du texte pour l'affichage ; valeurs possibles :
    *  page_id : ID de la page
    *  page_status : status de la page
    *  page_url : URL de la page
    *  page_name : nom de la page

**Exemples**

.. code:: php

    <?php $plxShow->pageBlog() ?>

.. code:: php

    <?php $plxShow->pageBlog('<li id="#page_id">
    <a class="#page_status" href="#page_url" title="#page_name">#page_name</a></li>') ?>

pageTitle
---------

**Usage**

.. code:: php

    <?php $plxShow->pageTitle() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->pageTitle() ?>

*Note*

* Cette fonction sert principalement à remplir automatiquement le champ TITLE de la balise `<head></head>` pour la page courante.
* Lors de la rédaction d'un article, vous pouvez personnaliser le contenu de cette balise.

pagination
----------

**Usage**

.. code:: php

    <?php $plxShow->pagination() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->pagination() ?>

racine
------

**Usage**

.. code:: php

    <?php $plxShow->racine() ?>

**Détail des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->racine() ?>

Si la "Racine du site" est définie sur http://example.org/, alors cette fonction affichera :

.. code:: none

    http://example.org/

Si la "Racine du site" est définie sur http://example.org/pluxml/, alors cette fonction affichera :

.. code:: none

    http://example.org/pluxml/

**Exemple avancé**

Une alternative à la fonction mainTitle :

.. code:: html

    <a href="<?php $plxShow->racine() ?>">Mon super site</a>

staticContent
-------------

**Usage**

.. code:: php

    <?php $plxShow->staticContent() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->staticContent() ?>

staticDate
----------

**Usage**

.. code:: php

    <?php $plxShow->staticDate('$format') ?>

**Détails des paramètres**

* **$format** (string) (optionnel) : format du texte de la date ; valeurs possibles :
    *  minute : affiche les minutes
    *  hour : affiche l'heure
    *  day : affiche le jour (lundi, mardi, ...)
    *  month : affiche le mois (janvier, février, ...)
    *  num_day : affiche le numéro du jour (1, 15, 31)
    *  num_month : affiche le numéro du mois (1, 6, 12)
    *  num_year(4) : affiche l'année au format long (ex: 2012)
    *  num_year(2) : affiche l'année au format court (ex: 12)
    *  valeur libre : caractère libre

**Exemples**

.. code:: php

    <?php $plxShow->staticDate('#day #num_day #month #num_year(4)') ?>

.. code:: php

    <?php $plxShow->staticDate('#num_day/#num_month/#num_year(4)') ?>

staticGroup
-----------

**Usage**

.. code:: php

    <?php $plxShow->staticGroup() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->staticGroup() ?>

staticId
--------

**Usage**

.. code:: php

    <?php $plxShow->staticId() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->staticId() ?>

**Exemple avancé**

.. code:: php

    <?php
        $var = $plxShow->staticId();
        echo $var;
    ?>

staticInclude
-------------

**Usage**

.. code:: php

    <?php $plxShow->staticInclude($id) ?>

**Détails des paramètres**

* **$id** (integer) (requis) : ID de la page statique à inclure

**Exemple**

Pour intégrer le contenu de la page statique ayant pour ID 1 :

.. code:: php

    <?php $plxShow->staticInclude(1) ?>

staticList
----------

**Usage**

.. code:: php

    <?php $plxShow->staticList('$extra','$format','$format_group') ?>

**Détails des paramètres**

* **$extra** (string) (optionnel) : nom du lien vers la page d'accueil
* **$format** (string) (optionnel) : format du texte pour chaque page : valeurs possibles :
    *  static_id : ID de la page statique
    *  static_status : status de la page statique (active / noactive)
    *  static_url : URL de la page statique
    *  static_name : nom de la page statique
    *  static_class : class (CSS) d'une page statique (valeur : static menu [si la page appartient à un groupe] ou static-group [si la page n'appartient pas à un groupe])
* **$format_group** (string) (optionnel) : format du texte pour chaque groupe de pages : valeurs possibles :
    *  group_id : ID d'un groupe de pages statiques
    *  group_class : class (CSS) d'un groupe de pages statiques (valeur : static-group)
    *  group_name : nom d'un groupe de pages statiques

**Exemples**

.. code:: php

    <?php $plxShow->staticList() ?>

.. code:: php

    <?php $plxShow->staticList('accueil','<li id="#static_id" class="#static_class">
    <a href="#static_url" class="#static_status" title="#static_name">#static_name</a></li>') ?>

.. code:: php

    <?php $plxShow->staticList('','<li id="#static_id" class="#static_class">
    <a href="#static_url" class="#static_status" title="#static_name">#static_name</a></li>'),
    '<li id="#group_id" class="#group_class">GROUPE : #group_name</li>') ?>

*Note* : notez les guillemets simples vides '' pour **$extra** ; ils sont obligatoires quand on ne veut pas de lien vers la page d'accueil mais qu'on personnalise **$format** ou **$format_group**

staticTitle
-----------

**Usage**

.. code:: php

    <?php $plxShow->staticTitle() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->staticTitle() ?>

staticUrl
---------

**Usage**

.. code:: php

    <?php $plxShow->staticUrl() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->staticUrl() ?>

subTitle
--------

**Usage**

.. code:: php

    <?php $plxShow->subTitle() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->subTitle() ?>

tagFeed
-------

**Usage**

.. code:: php

    <?php $plxShow->tagFeed('$type', '$tag', '$format') ?>

**Détails des paramètres**

* **$type** (string) (OBSOLETE - requis, vide) : type de flux
* **$tag** (string) (optionnel) : le mot clé
* **$format** (string) (optionnel) : format du lien ; valeurs possibles :
    *  feedUrl : url du flux RSS
    *  feedTitle : valeur de la constante L_ARTFEED_RSS_TAG
    *  feedName : valeur de la constante L_ARTFEED_RSS_TAG

**Exemple**

.. code:: php

    <?php $plxShow->tagFeed() ?>

.. code:: php

    <?php $plxShow->tagFeed('','pluxml','<a href="#feedUrl" title="#feedTitle">#feedName</a>') ?>

*Note* : les guillemets simples sont obligatoires quand on précise l'ID de l'article en raison du paramètre $type obsolète

tagList
-------

**Usage**

.. code:: php

    <?php $plxShow->tagList('$format', '$max', '$order') ?>

**Détails des paramètres**

* **$format** (string) (optionnel) : format du texte pour chaque tag ; valeurs possibles :
    *  tag_status : status du tag (active / noactive)
    *  tag_url : URL du tag
    *  tag_name : nom du tag
    *  nb_art : nombre d'article dans ce tag
* **$max** (integer) (optionnel) : nombre max de tags à afficher
* **$order** (string) (optionnel) : tri des tags (random, alpha, '' = tri par popularité)

**Exemples**

.. code:: php

    <?php $plxShow->tagList(
      '<li><a class="#tag_status" href="#tag_url" title="#tag_name">#tag_name</a></li>') ?>

.. code:: php

    <?php $plxShow->tagList(
      '<li><a class="#tag_status" href="#tag_url" title="#tag_name">#tag_name</a></li>', '10', 'alpha') ?>

tagName
-------

**Usage**

.. code:: php

    <?php $plxShow->tagName('$type') ?>

**Détails des paramètres**

* **$type** (string) (optionnel) : type d'affichage, soit sous forme d'un lien soit en texte seul ; valeur possible : 'link'

**Exemples**

.. code:: php

    <?php $plxShow->tagName() ?>

.. code:: php

    <?php $plxShow->tagName('link') ?>

**Exemple avancé**

Pour afficher le nom du tag dans la page tag, dans le fichier **/themes/mon-themes/tags.php** :

.. code:: none

    <h2>Tag : <?php $plxShow->tagName() ?></h2>
    <#-- la boucle des derniers articles -->

templaceCss
-----------

**Usage**

.. code:: php

    <?php $plxShow->templateCss('$css_dir') ?>

**Détails des paramètres**

* **$css_dir** (string) (requis) : répertoire de stockage des fichiers css (avec un / à la fin)

*Note* : manque de précision

**Exemple**

.. code:: php

    <?php $plxShow->templateCss() ?>

template
--------

**Usage**

.. code:: php

    <?php $plxShow->template() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->template() ?>

**Exemple avancé**

Cet exemple affichera l'image contenue dans **/themes/mon-theme/img/image.png** :

.. code:: html

    <img src="<?php $plxShow->template() ?>/img/image.png" />

urlRewrite
----------

**Usage**

.. code:: php

    <?php $plxShow->urlRewrite('$url') ?>

**Détail des paramètres**

* **$url** (string) (requis) : url à réécrire

**Exemple**

.. code:: php

    <a href="<?php $plxShow->urlRewrite('feed.php?rss') ?>">RSS</a>

version
-------

**Usage**

.. code:: php

    <?php $plxShow->version() ?>

**Détails des paramètres**

aucun

**Exemple**

.. code:: php

    <?php $plxShow->version() ?>
