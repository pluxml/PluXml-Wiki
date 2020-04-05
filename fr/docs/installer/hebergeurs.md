# Faire fonctionner PluXml chez vos hébergeurs

## Activer PHP5 sur votre hébergement

Depuis la version 5.0 de PluXml, il est obligatoire que votre hébergeur utilise PHP5. Par défaut, de nombreux serveurs sont encore paramétrés avec PHP4. Cela peut occasionner des messages d'erreur de type :

    Warning: cannot yet handle MBCS in html_entity_decode()# in /.../core/lib/class.plx.utils.php on line 408

ou

    Parse error: syntax error, unexpected T_STRING, expecting T_OLD_FUNCTION or T_FUNCTION or T_VAR or '}' in class.plx.utils.php on line 16

Pour activer PHP5 et faire fonctionner correctement votre PluXml 5+, suivre cette méthode :

* Créer sur votre ordinateur un fichier .htaccess
* Recopier dans ce fichier la directive pour activer PHP5 en fonction de votre hébergeur (voir liste plus bas)
* Uploader le fichier .htaccess sur votre site à la racine de PluXml

!!! note
    Windows n'autorise pas de créer des fichiers commençant par le caractère ".". Il faut donc:

    * Créer sur votre ordinateur un fichier htaccess.txt
    * Recopier dans ce fichier la directive pour activer PHP5 en fonction de votre hébergeur (voir liste plus bas)
    * Uploader le fichier htaccess.txt sur votre site à la racine de PluXml
    * Renommer le fichier htaccess.txt en .htaccess

__Liste des directives pour activer PHP5 selon l'hébergeur__

Ces directives sont à mettre dans votre fichier .htaccess sauf, pour OVH depuis fin 2014.

[__OVH__](http://www.ovh.com/) [source](https://www.ovh.com/fr/xml_shared/contentManager/guides/guide_1207.xml)

Sur un mutualisé chez OVH, fin 2014, il faut obligatoirement utiliser le fichier .ovhconfig présent à la racine de l’hébergement le .htaccess est obsolète.

Contenu du fichier :

    app.engine=php
    app.engine.version=5.5
    http.firewall=none
    environment=production

Pour changer de version PHP il suffira de jouer avec les versions en remplaçant le numéro de version :

[__1and1__])(http://1and1.fr)

    AddType x-mapp-php5 .php

[__Free__](http://free.fr)

    php 1

[__Online.net__](http://www.online.net/)

    AddType application/x-httpd-php5 .php

Nécessite également un chmod 755 sur le dossier d'installation de PluXml

[__Nuxit__](http://www.nuxit.com/)

    options -indexes
    AddHandler x-httpd-php5 .php
    AddType application/x-httpd-php5 .php

## Les sessions chez FREE

Vous remarquerez qu'en étant hébergé par FREE, les sessions ne fonctionnent pas par défaut (impossible d'accéder à l'administration). L'erreur courante se manifeste par un message d'erreur de ce type:

    Warning: session_start() [function.session-start]: open(/mnt/136/sdd/e/c/mon-site/
    sessions/sess_047bf89f882a9c970aa4cd06bc6d5c64, O_RDWR) failed: No such file or
    directory (2) in /mnt/136/sdd/e/c/mon-site/core/admin/prepend.php on line 39

    Warning: Unknown: Failed to write session data (files). Please verify that the
    current setting of session.save_path is correct (/mnt/136/sdd/e/c/mon-site/sessions)
    in Unknown on line 0

Pour résoudre ce problème, il vous faudra créer un répertoire vide nommé *sessions* à la racine de votre hébergement.

## Activer l'extension JSON chez FREE

Pour activer la prise en compte de l'extension JSON sur free.fr, créez un fichier .htaccess à la racine de votre site et collez (ou rajoutez au début du fichier) la ligne suivante:

    php56 1

## Les sessions chez NUXIT

Il faut créer un répertoire "session" sans "s" à la racine du site.

## Les sessions chez l'hébergeur chez.com

Il faut créer un répertoire "sessions" à la racine du site.

## Les droits chez OVH

* 604 pour tous les fichiers
* 705 pour tous les dossiers/sous-dossiers
