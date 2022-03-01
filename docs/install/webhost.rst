Faire fonctionner PluXml sur un hébergement mutualisé
=====================================================

Installation simplifiée
-----------------------

* alwaysdata (gratuit) : installation 1-click depuis la `Marketplace <https://www.alwaysdata.com/fr/marketplace/pluxml/>`_

Modifier la version de PHP
--------------------------

Depuis la version 5.8 de PluXml, il est obligatoire que votre hébergeur utilise PHP en version 5.6.
Par défaut, de nombreux hébergeurs sont encore paramétrés avec des versions de PHP inférieur à la 5.6. Cela peut occasionner des messages d'erreur de type :

.. code:: none

    Warning: cannot yet handle MBCS in html_entity_decode()# in /.../core/lib/class.plx.utils.php on line 408

ou

.. code:: none

    Parse error: syntax error, unexpected T_STRING, expecting T_OLD_FUNCTION or T_FUNCTION or T_VAR or '}'
    in class.plx.utils.php on line 16

Pour activer PHP 5.6 et faire fonctionner correctement PluXml :

* Créer sur votre ordinateur un fichier ``.htaccess``
* Copier dans ce fichier la directive permettant d'activer PHP 5 en fonction de votre hébergeur (voir liste plus bas)
* Uploader le fichier ``.htaccess`` sur votre site à la racine de PluXml

.. note::
    Windows n'autorise pas de créer des fichiers commençant par le caractère ".". Il faut donc:

    * Créer sur votre ordinateur un fichier ``htaccess.txt``
    * Copier dans ce fichier la directive pour activer PHP 5 en fonction de votre hébergeur (voir liste plus bas)
    * Uploader le fichier ``htaccess.txt`` sur votre site à la racine de PluXml
    * Renommer le fichier ``htaccess.txt`` en ``.htaccess``

Liste des directives pour utiliser PHP 5 selon l'hébergeur
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ces directives sont à mettre dans votre fichier ``.htaccess`` **sauf, pour OVH depuis fin 2014**.

**OVH** `(source) <https://www.ovh.com/fr/xml_shared/contentManager/guides/guide_1207.xml>`_

Sur un mutualisé chez OVH, depuis fin 2014, il faut obligatoirement utiliser le fichier ``.ovhconfig`` présent à la racine de l’hébergement
le ``.htaccess`` est obsolète.

Contenu du fichier :

.. code:: none

    app.engine=php
    app.engine.version=5.5
    http.firewall=none
    environment=production

Pour changer de version PHP il suffira de jouer avec les versions en remplaçant le numéro de version :

**1and1**

.. code:: none

    AddType x-mapp-php5 .php

**Free**
.. code:: none

    php 1

**Online.net**

.. code:: none

    AddType application/x-httpd-php5 .php

Nécessite également un chmod 755 sur le dossier d'installation de PluXml

**Nuxit**

.. code:: none

    options -indexes
    AddHandler x-httpd-php5 .php
    AddType application/x-httpd-php5 .php

Gestion des sessions
--------------------

Sur certains hébergeurs, les sessions ne fonctionnent pas par défaut. La connexion à l'administration de fonctionne pas.
L'erreur courante se manifeste par un message d'erreur de ce type:

.. code:: none

    Warning: session_start() [function.session-start]: open(/mnt/136/sdd/e/c/mon-site/
    sessions/sess_047bf89f882a9c970aa4cd06bc6d5c64, O_RDWR) failed: No such file or
    directory (2) in /mnt/136/sdd/e/c/mon-site/core/admin/prepend.php on line 39

    Warning: Unknown: Failed to write session data (files). Please verify that the
    current setting of session.save_path is correct (/mnt/136/sdd/e/c/mon-site/sessions)
    in Unknown on line 0

**Free**

Pour résoudre ce problème, il vous faudra créer un répertoire vide nommé ``sessions`` à la racine de votre hébergement.

**Chez.com**

Pour résoudre ce problème, il vous faudra créer un répertoire vide nommé ``sessions`` à la racine de votre hébergement.

**NUXIT**

Pour résoudre ce problème, il vous faudra créer un répertoire vide nommé ``session`` à la racine de votre hébergement.

Activer l'extension JSON chez FREE
----------------------------------

Pour activer la prise en compte de l'extension JSON sur free.fr, créez un fichier ``.htaccess`` à la racine de votre site et collez
(ou rajoutez au début du fichier) la ligne suivante:

.. code:: none

    php56 1

Les droits chez OVH
-------------------

* 604 pour tous les fichiers
* 705 pour tous les dossiers/sous-dossiers
