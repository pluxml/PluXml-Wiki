# Documentation de plxShow

Toutes les fonctions offertes par PluXml pour personnaliser votre thème.

La classe __plxShow__ est responsable de l'affichage. Elle permet donc de modifier cet affichage, ce qui se fait grâce à des fonctions prédéfinies.

Vous trouverez dans le menu de droite ces différentes fonctions qui vous permettront de modifier l'affichage par défaut de PluXml.

__Usage__

Le principe général pour utiliser la classe __plxShow__ est le suivant :

    <?php $plxShow->nomFonction() ?>

Certaines fonctions possèdent des variables prédéfinies, l'usage général devient ainsi :

    <?php $plxShow->nomFonction('$variable') ?>


## fuction archList

__Usage__

    <?php $plxShow->archList('$format') ?>

__Détails des paramètres__

* __$format__ (string) (optionnel) : format du texte pour l'affichage ; valeurs possibles :
    * archives_id : affiche l'ID de l'archive
    * archives_status : affiche le status de l'archive (active / noactive)
    * archives_nbart : affiche le nombre d'articles
    * archives_url : affiche l'URL de l'archive
    * archives_name : affiche le nom de l'archive (mois + année)
    * archives_month : affiche le mois de l'archive
    * archives_year : affiche l'année de l'archive
    * valeur libre : caractère libre

__Exemples__

    <?php $plxShow->archList() ?>
    <?php $plxShow->archList('<li id="#archives_id"><a class="#archives_status" href="#archives_url" title="#archives_name">#archives_name (#archives_nbart)</a></li>') ?>

## fuction artAuthorEmail

__Usage__

    <?php $plxShow->artAuthorEmail() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->artAuthorEmail() ?>

## fuction artAuthorInfos

__Usage__

    <?php $plxShow->artAuthorInfos('$format') ?>

__Détails des paramètres__

* __$format__ (string) (optionnel) : permet de préciser une mise en page. Formatage par défaut : `<div class="author-infos"></div>`. Valeur disponible :
    *  art_authorinfos : permet d'afficher les informations sur l'auteur  (utile quand on personnalise la mise en page)

__Exemples__

    <?php $plxShow->artAuthorInfos() ?>
    <?php $plxShow->artAuthorInfos('<div>#art_authorinfos</div>') ?>

## fuction artAuthor

__Usage__

    <?php $plxShow->artAuthor($echo) ?>

__Détails des paramètres__

* __$echo__ (boolean) (optionnel) : valeurs possibles : true / false. Par défaut la valeur est à true. Si la valeur est à false, alors le nom de l'auteur ne sera pas affiché

__Exemples__

    <?php $plxShow->artAuthor() ?>
    <?php $plxShow->artAuthor(true) ?>
    <?php $plxShow->artAuthor(false) ?>

## fuction artCatId

__Usage__

    <?php $plxShow->artCatId() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->artCatId() ?>

__Exemple avancé__

    <?php
        $var = $plxShow->artCatId();
        echo $var;
    ?>

## fuction artCat

__Usage__

    <?php $plxShow->artCat('$separator') ?>

__Détails des paramètres__

* __$separator__ (string) (optionnel) : caractère de séparation entre les catégories affichées ; valeur par défaut : ','

__Exemple__

    <?php $plxShow->artCat('|') ?>

## fuction artChapo

__Usage__

    <?php $plxShow->artChapo('$format',$content) ?>

__Détails des paramètres__

* __$format__ (string) (optionnel) : format d'affichage du lien pour lire la suite de l'article ; valeur par défaut : #art_title ; valeurs possibles :
    *  art_title : affiche le titre de l'article dans le lien "pour lire la suite" de l'article
    *  valeur libre : chaîne de caractère de son choix
* __$content__ (boolean) (optionnel) : affichage oui ou non le contenu de l'article si le chapô est vide ; valeur par défaut : true ; valeurs possibles : true / false ; *Note* : si la valeur est à false, alors $format ne sera pas affiché.

__Exemples__

    <?php $plxShow->artChapo('#art_title',true) ?>
    <?php $plxShow->artChapo('Continuer la lecture',true) ?>

## fuction artContent

__Usage__

    <?php $plxShow->artContent($chapo) ?>

__Détails des paramètres__

* __$chapo__ (boolean) (requis) : affiche oui ou non le chapô ; valeurs possible : true / false ; valeur par défaut : true

__Exemples__

    <?php $plxShow->artContent() ?>
    <?php $plxShow->artContent(true) ?>
    <?php $plxShow->artContent(false) ?>

## fuction artDate

__Usage__

    <?php $plxShow->artDate('$format') ?>

__Détails des paramètres__

* __$format__ (string) (optionnel) : format de la date ; valeurs par défaut : '#day #num_day #month #num_year(4)' ; valeurs possibles :
    *  minute : affiche les minutes
    *  hour : affiche l'heure de publication
    *  day : affiche le jour (au format texte : lundi, mardi, etc...)
    *  month : affiche le mois (au format texte : janvier, février, mars, etc...)
    *  num_day : affiche le numéro du jour du mois (1, 15, ..., 31,)
    *  num_month : affiche le numéro du mois (1, 2, 5, ..., 12)
    *  num_year(4) : affiche l'année sur 4 chiffres (ex: 2012)
    *  num_year(2) : affiche l'année sur 2 chiffres (ex: 12)
    *  valeur libre : chaîne de caractère de son choix

__Exemples__

    <?php $plxShow->artDate() ?>
    <?php $plxShow->artDate('#num_day #month #num_year(4)') ?>

__Exemples avancés__

Formatage avancé avec des caractères libres :

    <?php $plxShow->artDate('#hour:#minute') ?>
    <?php $plxShow->artDate('#num_day/#num_month/#num_year(4)') ?>

## fuction  artFeed

__Usage__

    <?php $plxShow->artFeed('$type',$categorie,'$format') ?>

__Détails des paramètres__

* __$type__ (obsolete)
* __$categorie__ (integer) (optionnel) : identifiant (ID sans les 0) d'une catégorie
* __$format__ (string) (optionnel) : format du lien ; valeurs possibles :
    *  feedUrl : url du flux RSS
    *  feedName : nom du flux RSS

__Exemples__

Flux RSS des articles de tout le site :

    <?php $plxShow->artFeed() ?>

Flux RSS des articles de la catégorie 1 :

    <?php $plxShow->artFeed('',1, '<a href="#feedUrl" title="#feedTitle">#feedName</a>') ?>

*Note* : les guillemets simples vides ('') sont obligatoires quand on précise une catégorie, à cause du paramètre obsolete __$type__

## fuction artId

__Usage__

    <?php $plxShow->artId() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->artId() ?>

__Exemple avancé__

    <?php
        $var = $plxShow->artId();
        echo $var;
    ?>

## fuction artNbCom

__Usage__

    <?php $plxShow->artNbCom('$f1','$f2','$f3') ?>

__Détails des paramètres__

* __$f1__ (string) (optionnel) : format d'affichage si nombre de commentaire = 0 ; variable possible : #nb pour afficher le nombre de commentaire ; valeur par défaut 'aucun commentaire'
* __$f2__ (string) (optionnel) : format d'affichage si nombre de commentaire = 1 ; variable possible : #nb pour afficher le nombre de commentaire ; valeur par défaut '#nb commentaire'
* __$f2__ (string) (optionnel) : format d'affichage si nombre de commentaire > 1 ; variable possible : #nb pour afficher le nombre de commentaires ; valeur par défaut '#nb commentaires'

__Exemples__

    <?php $plxShow->artNbCom() ?>
    <?php $plxShow->artNbCom('#nb commentaire','#nb commentaire','#nb commentaires') ?>
    <?php $plxShow->artNbCom('#nb','#nb','#nb') ?>

## fuction artTags

__Usage__

    <?php $plxShow->artTags('$format','$separor') ?>

__Détails des paramètres__

* __$format__ (string) (optionnel) : format du texte pour chaque tag ; valeurs par défauts : `<a class="#tag_status" href="#tag_url" title="#tag_name">#tag_name</a>` ; valeurs possibles :
    *  tag_status : permet d'ajouter 'class="noactive"' ou 'class="active"' à l'attribut HTML 'a' (permet de définir un style CSS quand un tag est actif, c'est à dire consulté)
    *  tag_url : l'URL du tag
    *  tag_name : le nom du tag
* __$separator__ (string) (optionnel) : caractère de séparation entre les tags affichées ; valeur par défaut : ','

__Exemples__

    <?php $plxShow->artTags('<a class="#tag_status" href="#tag_url" title="#tag_name">#tag_name</a>',',') ?>
    <?php $plxShow->artTags('<a href="#tag_url" title="#tag_name">#tag_name</a>',' |') ?>

__Exemple avancé__

    <ul>
        <?php $plxShow->artTags('<li><a href="#tag_url" title="#tag_name">#tag_name</a></li>','') ?>
    </ul>
## function artTitle

__Usage__

    <?php $plxShow->artTitle('$type') ?>

__Détails des paramètres__

* __$type__ (string) (optionnel) : valeur possible : 'link'. Affiche le titre de l'article sous forme d'un lien cliquable

__Exemples__

    <?php $plxShow->artTitle() ?>
    <?php $plxShow->artTitle('link') ?>
    
## function artThumbnail

__Usage__

    <?php $plxShow->artThumbnail('$format', $echo); ?>

__Détails des paramètres__

* __$format__ (string) (optionnel) : format du texte pour chaque tag ; valeurs par défauts : `<a href="#img_url"><img class="art_thumbnail" src="#img_thumb_url" alt="#img_alt" title="#img_title" /></a>` ; valeurs possibles :
    *  img_url : l'URL de l'image d'accroche
    *  img_thumb_url : l'URL de la miniature de l'image d'accroche
    *  img_title : Titre de l'image d'accroche
    *  img_alt : Texte alternatif d'affichage de l'image d'accroche
* __$echo__ (boolean) (optionnel) : valeurs possibles : true / false. Par défaut la valeur est à true. Si la valeur est à false, alors l'image ne sera pas affiché
* __$article__ (boolean) (optionnel) : valeurs possibles : true / false. Par défait la valeur est false. Si la valeur est true, alors au clic sur l'image PluXml redirige vers l'article et non vers l'image.

__Exemples__

    <?php $plxShow->artThumbnail() ?>
    <?php $plxShow->artThumbnail('<a href="#img_url"><img class="art_thumbnail" src="#img_thumb_url" alt="#img_alt" title="#img_title" /></a>', true) ?>

## function artUrl

__Usage__

    <?php $plxShow->artUrl() ?>

__Détails des paramètres__

* __$type__ (deprecated) : lien relatif ou absolu

__Exemple__

    <?php $plxShow->artUrl() ?>

__Exemple avancé__

Partager facilement un article sur les réseaux sociaux :

    <a href="http://www.facebook.com/sharer.php?u=<?php $plxShow->artUrl() ?>">Partager sur Facebook</a>

## function callHook

__Usage__

    <?php $plxShow->callHook('$hookName','$parms') ?>

__Détails des paramètres__

* __$hookName__ (string) (requis) : nom du hook
* __$parms__ (string) (requis) : paramètre ou liste de paramètres sous forme de array

__Exemple__

Sans return, passage d'un paramètre :

    <?php eval($plxShow->callHook('MyPluginFunction', 'AZERTY')); ?>

Avec return, passage de 2 paramètres à faire sous forme de tableau :

    <?php $b = $plxShow->callHook('MyPluginFunction', array('AZERTY', 'QWERTY')); ?>

## function capchaQ

__Usage__

    <?php $plxShow->capchaQ() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->capchaQ() ?>

## function capchaR

__Usage__

    <?php $plxShow->capchaR() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->capchaR() ?>

## function catDescription

__Usage__

    <?php $plxShow->catDescription() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->catDescription() ?>

## function catId

__Usage__

    <?php $plxShow->catId() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->catId() ?>

__Exemple avancé__

    <?php
        $var = $plxShow->catId();
        echo $var;
    ?>

## function catList

__Usage__

    <?php $plxShow->catList('$extra','$format','include','exclude') ?>

__Détails des paramètres__

* __$extra__ (string) (requis) : nom du lien vers la page d'accueil ; si on ne veut pas de lien vers la page d'accueil, mettre des guillemets simples vides ('')
* __$format__ (string) (requis) : format du texte pour chaque catégorie ; valeurs possibles :
    *  cat_id : ID de la catégorie
    *  cat_status : statut de la catégorie (active, noactive)
    *  cat_url : url de la catégorie
    *  cat_name : nom de la catégorie
    *  art_nb : nombre d'articles dans cette catégorie
* __$include__ (integer) (optionnel) : liste des catégories à afficher séparées par le caractère '|'
* __$exclude__ (integer) (optionnel) : liste des catégories à ne pas afficher séparées par le caractère '|' ; si renseigné, $include doit contenir des guillements simples vides

__Exemples__

    <?php $plxShow->catList('Accueil','<li><a href="#cat_url" title="#cat_name">#cat_name</a></li>'); ?>
    <?php $plxShow->catList('','<li id="#cat_id" class="#cat_status"><a href="#cat_url" title="#cat_name">#cat_name</a> (#art_nb)</li>'); ?>

*Note* : on notera les guillemets simples vides '' obligatoires quand on ne veut pas de lien vers la page d'accueil.

L'exemple suivant n'affichera que la catégorie numéro 1 :

    <?php $plxShow->catList('','<li><a href="#cat_url" title="#cat_name">#cat_name</a></li>',1); ?>

L'exemple suivant affichera toutes les catégories __sauf__ la catégorie numéro 2 :

    <?php $plxShow->catList('','<li><a href="#cat_url" title="#cat_name">#cat_name</a></li>','',2); ?>

__Exemple avancé__

Il est possible de passer une variable dans les paramètres :

    <?php
        $catInclude = 3;
        $plxShow->catList('','<li><a href="#cat_url" title="#cat_name">#cat_name</a></li>',$catInclude);
    ?>

    <?php
        $homeTitle = 'Accueil';
        $plxShow->catList($homeTitle,'<li><a href="#cat_url" title="#cat_name">#cat_name</a></li>');
    ?>

Voyons à présent un exemple avec la fonction mode :

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

## function catName

__Usage__

    <?php $plxShow->catName('$type') ?>

__Détails des paramètres__

* __$type__ (string) (optionnel) : valeur possible : 'link'. Affiche le nom de la catégorie sous forme d'un lien cliquable

__Exemples__

    <?php $plxShow->catName() ?>
    <?php $plxShow->catName('link') ?>

## function catThumbnail

__Usage__

    <?php $plxShow->catThumbnail('$format', $echo); ?>

__Détails des paramètres__

* __$format__ (string) (optionnel) : format du texte pour chaque tag ; valeurs possibles :
    *  img_url : l'URL de l'image d'accroche
    *  img_thumb_url : l'URL de la miniature de l'image d'accroche
    *  img_title : Titre de l'image d'accroche
    *  img_alt : Texte alternatif d'affichage de l'image d'accroche
* __$echo__ (boolean) (optionnel) : valeurs possibles : true / false. Par défaut la valeur est à true. Si la valeur est à false, alors l'image ne sera pas affichée

__Exemples__

    <?php $plxShow->catThumbnail() ?>
    <?php $plxShow->catThumbnail('<a href="#img_url"><img class="cat_thumbnail" src="#img_thumb_url" alt="#img_alt" title="#img_title" /></a>', true) ?>

## function catUrl

__Usage__

    <?php $plxShow->catUrl($id) ?>

__Détails des paramètres__

* __$id__ (integer) (requis) : id de la categorie sous la forme numérique ou formatée (ex: 1 ou 001)

__Exemple__

    <?php $plxShow->catUrl(1) ?>

__Exemple avancé__

    <?php
        $var = $plxShow->catUrl(1);
        echo $var;
    ?>

Cet exemple affichera *http://example.org/categorie1/nom-de-ma-categorie*

## function charset

__Usage__

    <?php $plxShow->charset('$casse'); ?>

__Détails des paramètres__

* __$casse__ (string) (optionnel) : la $casse est soit 'min' soit 'maj'. Par défaut 'min'.

__Exemples__

    <?php $plxShow->charset(); ?>

Affichera par exemple :

    utf-8

Autre exemple

    <?php $plxShow->charset('maj'); ?>

Affichera par exemple :

    UTF-8

__Exemple avancé__

    <meta http-equiv="Content-Type" content="text/html; charset=<?php $plxShow->charset(); ?>" />

## function chrono

__Usage__

    <?php $plxShow->chrono() ?>

__Détails des paramètres__

aucun

__Exemple__

    <p>Page générée en <?php $plxShow->chrono() ?></p>

## function comAuthor

__Usage__

    <?php $plxShow->comAuthor('$type') ?>

__Détails des paramètres__

* __$type__ (string) (optionnel) : affiche le nom de l'auteur sous forme de lien vers son site ; valeur possible : 'link' ;

__Exemples__

    <?php $plxShow->comAuthor() ?>
    <?php $plxShow->comAuthor('link') ?>

## function comContent

__Usage__

    <?php $plxShow->comContent() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->comContent() ?>

## function comDate

__Usage__

    <?php $plxShow->comDate('$format') ?>

__Détails des paramètres__

* __$format__ (string) (optionnel) : format du texte de la date ; valeurs possibles :
    *  minute : affiche les minutes
    *  hour : affiche l'heure
    *  day : affiche le nom du jour (lundi, mardi, etc...)
    *  month : affiche le nom du mois (janvier, février, etc...)
    *  num_day : affiche le numéro du jour (01, 15, 31)
    *  num_month : affiche le numéro du mois (01, 06, 12)
    *  num_year(2) : affiche l'année au format court (ex: 12)
    *  num_year(4) : affiche l'année au format long (ex: 2012)
    *  valeur libre : un caractère au choix

__Exemples__

    <?php $plxShow->comDate('#day #num_day #month #num_year(4)') ?>
    <?php $plxShow->comDate('#num_day/num_#month/#num_year(4)') ?>

## function comFeed

__Usage__

    <?php $plxShow->comFeed('$type',$article,'$format') ?>

__Détails des paramètres__

* __$type__ (string) (OBSOLETE - requis, vide) : type de flux
* __$article__ (integer) (optionnel) : identifiant (sans les 0) d'un article
* __$format__ (string) (optionnel) : format du lien ; valeurs possibles :
    *  feedUrl : url du flux RSS
    *  feedName : nom du flux RSS

__Exemple__

    <?php $plxShow->comFeed() ?>
    <?php $plxShow->comFeed('',3,'<a href="#feedUrl" title="#feedTitle">#feedName</a>') ?>

*Note* : les guillemets simples sont obligatoires quand on précise l'ID de l'article en raison du paramètre $type obsolète

## function comGet

__Usage__

    <?php $plxShow->comGet($key,'$defaut') ?>

*Note* : manque de précision

__Détails des paramètres__

* __$key__ (string) (requis) : clé du tableau GET
* __$defaut__ (string) (requis) : valeur par défaut si variable vide

__Exemple__

## function comId

__Usage__

    <?php $plxShow->comId() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->comId() ?>

## function comMessage

__Usage__

    <?php $plxShow->comMessage() ?>

*Note* : manque de précision

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->comMessage() ?>

## function comType

__Usage__

    <?php $plxShow->comType() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->comType() ?>

__Exemple avancé__

Cette fonction est utile pour un habillage CSS différent quand le commentaire est écrit par l'admin du site :

    <div class="<?php $plxShow->comType() ?>">ON AFFICHE ICI LE COMMENTAIRE</div>

## function comUrl

__Usage__

    <?php $plxShow->comUrl() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->comUrl() ?>

## function defaultLang

__Usage__

    <?php $plxShow->defaultLang($echo) ?>

__Détails des paramètres__

* __$echo__ (boolean) (optionnel) : si TRUE, affichage à l'écran

__Exemple__

    <?php $plxShow->defaultLang(true) ?>

## function erreurMessage

__Usage__

    <?php $plxShow->erreurMessage() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->erreurMessage() ?>

## function getLang

__Usage__

    <?php $plxShow->getLang('$key') ?>

__Détails des paramètres__

* __$key__ (string) (requis) : clé de traduction à afficher

__Exemple__

    <?php $plxShow->getLang('HOME') ?>

__Liste des termes__

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

## function get

__Usage__

    <?php $plxShow->get() ?>

*Note* : manque de précision

__Détail des paramètres__

aucun

__Exemple__

## function httpEncoding

__Usage__

    <?php $plxShow->httpEncoding() ?>

__Détail des paramètres__

aucun

__Exemple__

    <?php $plxShow->httpEncoding() ?>

Si la compression Gzip est activée dans les paramètres avancés de PluXml, alors cette fonction affichera :

    Compression GZIP activée

## function lang

__Usage__

    <?php $plxShow->lang('$key') ?>

__Détails des paramètres__

* __$key__ (string) (requis) : texte traduit par PluXml

__Exemple__

    <?php $plxShow->lang('CATEGORIES') ?>

__Liste des termes__

Vous pouvez trouver la liste dans termes dans les fichiers du répertoire __/themes/defaut/lang/__.

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

## function lastArtList

__Usage__

    <?php $plxShow->lastArtList('$format',$max,$cat_id,'$ending',$sort) ?>

__Détails des paramètres__

* __$format__ (string) (optionnel) : format du texte pour chaque article ; valeurs possibles :
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
* __$max__ (integer) (optionnel) : nombre d'article à afficher ; valeur par defaut : 5
* __$cat_id__ (integer) (optionnel) : limiter l'affiche des articles à une catégorie précise
* __$ending__ (string) (optionnel) : texte à ajouter en fin de ligne ; *Note* : ne semble pas fonctionner
* __$sort__ (string) (optionnel) : ordre de trie. Valeur possible sort|rsort|alpha|random

__Exemple__

    <?php $plxShow->lastArtList('<li><a href="#art_url" title="#art_title">#art_title</a></li>',3) ?>

Limiter l'affichage aux 5 derniers articles de la catégorie 1 :

    <?php $plxShow->lastArtList('<li><a href="#art_url" title="#art_title">#art_title</a></li>',5,1) ?>

## function lastComList

__Usage__

    <?php $plxShow->lastComList('$format',$max,$art_id,$cat_ids) ?>

__Détails des paramètres__

* __$format__ (string) (optionnel) : format du texte pour chaque commentaire ; valeurs possibles :
    *  com_id : affiche l'ID du commentaire
    *  com_url : affiche l'URL du commentaire
    *  com_author : affiche l'auteur du commentaire
    *  com_content(num) : affiche les N (num) premiers caractères du commentaire
    *  com_content : affiche le commentaire dans son intégralité
    *  com_date : affiche la date du commentaire
    *  com_hour : affiche l'heure de commentaire
    *  valeur libre : caractère libre
* __$max__ (integer) (optionnel) : nombre de commentaires maximum à afficher ; valeur par défaut : 5
* __$art_id__ (integer) (optionnel) : restreindre l'affichage des derniers commentaires à un article précis via son ID (ex: 24, 3)
* __$cat_ids__ (integer) (optionnel) : restreindre l'affichage des derniers commentaires à certaines catégories via leur ID (ex: 1|2 ; voir exemples)

__Exemples__

Affichage basique :

    <?php $plxShow->lastComList('<li><a href="#com_url">#com_author a dit :</a><p>#com_content(50)</p></li>') ?>

Afficher seulement les 3 derniers commentaires :

    <?php $plxShow->lastComList('<li><a href="#com_url">#com_author a dit :</a><p>#com_content(50)</p></li>',3) ?>

Afficher seulement les 3 derniers commentaires de l'article ayant l'ID 9 :

    <?php $plxShow->lastComList('<li><a href="#com_url">#com_author a dit :</a><p>#com_content(50)</p></li>',3,9) ?>

Afficher seulement les 3 derniers commentaires de la catégorie 6 :

    <?php $plxShow->lastComList('<li><a href="#com_url">#com_author a dit :</a><p>#com_content(50)</p></li>',3,'',6) ?>

*Note* : notez les guillements simples '' à la place de __$art_id__

Afficher seulement les 3 derniers commentaires des catégories 6 et 8 :

    <?php $plxShow->lastComList('<li><a href="#com_url">#com_author a dit :</a><p>#com_content(50)</p></li>',3,'',6|8) ?>

## function mainTitle

__Usage__

    <?php $plxShow->mainTitle('$type') ?>

__Détails des paramètres__

* __$type__ (string) (optionnel) : type d'affichage en format texte ou sous forme de lien ; valeur possible : link

__Exemples__

    <?php $plxShow->mainTitle() ?>
    <?php $plxShow->mainTitle('link') ?>

__Exemple avancé__

    <div id="header"><h1><?php $plxShow->mainTitle('link') ?></h1></div>

*Note*

* cette fonction définie le contenu et la cible du lien. Pour personnaliser le contenu du lien, voir la [fontion racine|plxShow-racine]

## function meta

__Usage__

    <?php $plxShow->meta('$meta') ?>

__Détails des paramètres__

* __$meta__ (string) (requis) : nom du meta à afficher ; les différentes valeurs possibles sont : description, keywords, author

__Exemples__

    <?php $plxShow->meta('description') ?>
    <?php $plxShow->meta('keywords') ?>
    <?php $plxShow->meta('author') ?>

*Note*

* Cette fonction sert principalement à remplir automatiquement les champs "meta" de la balise `<head></head>`
* Lors de la rédaction d'un article, vous pouvez indiquer le contenu des balises "description" et "keywords"

## function mode

__Usage__

    <?php $plxShow->mode() ?>

__Détail des paramètres__

aucun

__Exemple__

    <?php
        $var = $plxShow->mode();
        echo $var;
    ?>

Affichera soit home, article, categorie, static, archives ou tags.

__Exemple avancé__

    <?php
        $var = $plxShow->mode();
        if ($var == 'home') {
            echo "mode HOME";
        }
        else{
            echo "mode NON HOME";
        }
    ?>

## function nbAllArt

__Usage__

    <?php $plxShow->nbAllArt() ?>

__Détails des paramètres__

* __$f1__ (string) (optionnel) : format d'affichage si nombre d'article = 0 ; variable possible : `#nb` pour afficher le nombre d'article ; valeur par défaut 'aucun article'
* __$f2__ (string) (optionnel) : format d'affichage si nombre d'article = 1 ; variable possible : `#nb` pour afficher le nombre d'article ; valeur par défaut '#nb article'
* __$f2__ (string) (optionnel) : format d'affichage si nombre d'article > 1 ; variable possible : `#nb` pour afficher le nombre d'articles ; valeur par défaut '#nb articles'

__Exemples__

    <?php $plxShow->nbAllArt() ?>
    <?php $plxShow->nbAllArt('aucun article','#nb article publié','#nb articles au total') ?>

## function nbAllCom

__Usage__

    <?php $plxShow->nbAllCom('$f1','$f2','$f3') ?>

__Détails des paramètres__

* __$f1__ (string) (optionnel) : format d'affichage si nombre de commentaire = 0 ; valeur possible : `#nb` pour afficher le nombre de commentaire
* __$f2__ (string) (optionnel) : format d'affichage si nombre de commentaire = 1 ; valeur possible : `#nb` pour afficher le nombre de commentaire
* __$f3__ (string) (optionnel) : format d'affichage si nombre de commentaire > 0 ; valeur possible : `#nb` pour afficher le nombre de commentaire

__Exemples__

    <?php $plxShow->nbAllCom() ?>

    <?php $plxShow->nbAllCom('Aucun commentaire', '#nb commentaire', '#nb commentaires au total') ?>

## function pageBlog

__Usage__

    <?php $plxShow->pageBlog('$format') ?>

__Détails des paramètres__

* __$format__ (string) (optionnel) : format du texte pour l'affichage ; valeurs possibles :
    *  page_id : ID de la page
    *  page_status : status de la page
    *  page_url : URL de la page
    *  page_name : nom de la page

__Exemples__

    <?php $plxShow->pageBlog() ?>
    <?php $plxShow->pageBlog('<li id="#page_id"><a class="#page_status" href="#page_url" title="#page_name">#page_name</a></li>') ?>

## function pageTitle

__Usage__

    <?php $plxShow->pageTitle() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->pageTitle() ?>

*Note*

* Cette fonction sert principalement à remplir automatiquement le champ TITLE de la balise `<head></head>` pour la page courante.
* Lors de la rédaction d'un article, vous pouvez personnaliser le contenu de cette balise.

## function pagination

__Usage__

    <?php $plxShow->pagination() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->pagination() ?>

## function racine

__Usage__

    <?php $plxShow->racine() ?>

__Détail des paramètres__

aucun

__Exemple__

    <?php $plxShow->racine() ?>

Si la "Racine du site" est définie sur http://example.org/, alors cette fonction affichera :

    http://example.org/

Si la "Racine du site" est définie sur http://example.org/pluxml/, alors cette fonction affichera :

    http://example.org/pluxml/

__Exemple avancé__

Une alternative à la fonction mainTitle :

    <a href="<?php $plxShow->racine() ?>">Mon super site</a>

## function staticContent

__Usage__

    <?php $plxShow->staticContent() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->staticContent() ?>

## function staticDate

__Usage__

    <?php $plxShow->staticDate('$format') ?>

__Détails des paramètres__

* __$format__ (string) (optionnel) : format du texte de la date ; valeurs possibles :
    *  minute : affiche les minutes
    *  hour : affiche l'heure
    *  day : affiche le jour (lundi, mardi, ...)
    *  month : affiche le mois (janvier, février, ...)
    *  num_day : affiche le numéro du jour (1, 15, 31)
    *  num_month : affiche le numéro du mois (1, 6, 12)
    *  num_year(4) : affiche l'année au format long (ex: 2012)
    *  num_year(2) : affiche l'année au format court (ex: 12)
    *  valeur libre : caractère libre

__Exemples__

    <?php $plxShow->staticDate('#day #num_day #month #num_year(4)') ?>
    <?php $plxShow->staticDate('#num_day/#num_month/#num_year(4)') ?>

## function staticGroup

__Usage__

    <?php $plxShow->staticGroup() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->staticGroup() ?>

## function staticId

__Usage__

    <?php $plxShow->staticId() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->staticId() ?>

__Exemple avancé__

    <?php
        $var = $plxShow->staticId();
        echo $var;
    ?>

## function staticInclude

__Usage__

    <?php $plxShow->staticInclude($id) ?>

__Détails des paramètres__

* __$id__ (integer) (requis) : ID de la page statique à inclure

__Exemple__

Pour intégrer le contenu de la page statique ayant pour ID 1 :

    <?php $plxShow->staticInclude(1) ?>

## function staticList

__Usage__

    <?php $plxShow->staticList('$extra','$format','$format_group') ?>

__Détails des paramètres__

* __$extra__ (string) (optionnel) : nom du lien vers la page d'accueil
* __$format__ (string) (optionnel) : format du texte pour chaque page : valeurs possibles :
    *  static_id : ID de la page statique
    *  static_status : status de la page statique (active / noactive)
    *  static_url : URL de la page statique
    *  static_name : nom de la page statique
    *  static_class : class (CSS) d'une page statique (valeur : static menu [si la page appartient à un groupe] ou static-group [si la page n'appartient pas à un groupe])
* __$format_group__ (string) (optionnel) : format du texte pour chaque groupe de pages : valeurs possibles :
    *  group_id : ID d'un groupe de pages statiques
    *  group_class : class (CSS) d'un groupe de pages statiques (valeur : static-group)
    *  group_name : nom d'un groupe de pages statiques

__Exemples__

    <?php $plxShow->staticList() ?>

    <?php $plxShow->staticList('accueil','<li id="#static_id" class="#static_class"><a href="#static_url" class="#static_status" title="#static_name">#static_name</a></li>') ?>

    <?php $plxShow->staticList('','<li id="#static_id" class="#static_class"><a href="#static_url" class="#static_status" title="#static_name">#static_name</a></li>'),'<li id="#group_id" class="#group_class">GROUPE : #group_name</li>') ?>

*Note* : notez les guillemets simples vides '' pour __$extra__ ; ils sont obligatoires quand on ne veut pas de lien vers la page d'accueil mais qu'on personnalise __$format__ ou __$format_group__

## function staticTitle

__Usage__

    <?php $plxShow->staticTitle() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->staticTitle() ?>

## function staticUrl

__Usage__

    <?php $plxShow->staticUrl() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->staticUrl() ?>

## function subTitle

__Usage__

    <?php $plxShow->subTitle() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->subTitle() ?>

## function tagFeed

__Usage__

    <?php $plxShow->tagFeed('$type', '$tag', '$format') ?>

__Détails des paramètres__

* __$type__ (string) (OBSOLETE - requis, vide) : type de flux
* __$tag__ (string) (optionnel) : le mot clé
* __$format__ (string) (optionnel) : format du lien ; valeurs possibles :
    *  feedUrl : url du flux RSS
    *  feedTitle : valeur de la constante L_ARTFEED_RSS_TAG
    *  feedName : valeur de la constante L_ARTFEED_RSS_TAG

__Exemple__

    <?php $plxShow->tagFeed() ?>
    <?php $plxShow->tagFeed('','pluxml','<a href="#feedUrl" title="#feedTitle">#feedName</a>') ?>

*Note* : les guillemets simples sont obligatoires quand on précise l'ID de l'article en raison du paramètre $type obsolète

## function tagList

__Usage__

    <?php $plxShow->tagList('$format',$max) ?>

__Détails des paramètres__

* __$format__ (string) (optionnel) : format du texte pour chaque tag ; valeurs possibles :
    *  tag_status : status du tag (active / noactive)
    *  tag_url : URL du tag
    *  tag_name : nom du tag
    *  nb_art : nombre d'article dans ce tag
* __$format__ (integer) (optionnel) : nombre max de tags à afficher

__Exemples__

    <?php $plxShow->tagList('<li><a class="#tag_status" href="#tag_url" title="#tag_name">#tag_name</a></li>') ?>
    <?php $plxShow->tagList('<li><a class="#tag_status" href="#tag_url" title="#tag_name">#tag_name (#nb_art)</a></li>,3') ?>

## function tagName

__Usage__

    <?php $plxShow->tagName('$type') ?>

__Détails des paramètres__

* __$type__ (string) (optionnel) : type d'affichage, soit sous forme d'un lien soit en texte seul ; valeur possible : 'link'

__Exemples__

    <?php $plxShow->tagName() ?>
    <?php $plxShow->tagName('link') ?>

__Exemple avancé__

Pour afficher le nom du tag dans la page tag, dans le fichier __/themes/mon-themes/tags.php__ :

    <h2>Tag : <?php $plxShow->tagName() ?></h2>
    <#-- la boucle des derniers articles -->

## function templaceCss

__Usage__

    <?php $plxShow->templateCss('$css_dir') ?>

__Détails des paramètres__

* __$css_dir__ (string) (requis) : répertoire de stockage des fichiers css (avec un / à la fin)

*Note* : manque de précision

__Exemple__

    <?php $plxShow->templateCss() ?>

## function template

__Usage__

    <?php $plxShow->template() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->template() ?>

__Exemple avancé__

Cet exemple affichera l'image contenue dans __/themes/mon-theme/img/image.png__ :

    <img src="<?php $plxShow->template() ?>/img/image.png" />

## function urlRewrite

__Usage__

    <?php $plxShow->urlRewrite('$url') ?>

__Détail des paramètres__

* __$url__ (string) (requis) : url à réécrire

__Exemple__

    <a href="<?php $plxShow->urlRewrite('feed.php?rss') ?>">RSS</a>

## function version

__Usage__

    <?php $plxShow->version() ?>

__Détails des paramètres__

aucun

__Exemple__

    <?php $plxShow->version() ?>
