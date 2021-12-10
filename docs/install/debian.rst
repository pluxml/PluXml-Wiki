Installer depuis les dépôts Debian
==================================

PluXml est disponible sous la forme d'un `paquet Debian <http://packages.debian.org/pluxml>`_.

Intérêt
-------

Le paquet Debian de PluXml contient des informations de dépendances, qui permettent d'installer automatiquement tout ce dont PluXml a besoin pour fonctionner, c'est à dire un serveur web avec un interpréteur PHP.

Le paquet installe les fichiers et répertoires de PluXml avec des permissions appropriées, de façon à ce qu'aucune adaptation ne soit nécessaire après l'installation.

Ce paquet inclut également une série de questions de configuration, qui permettent de définir les paramètres initiaux du blog : titre, description, compte administrateur...

Enfin, les mises à jour sont prises en charge par le système de paquets Debian, c'est à dire que lorsqu'une mise à jour est publiée et intégrée à Debian (ce n'est pas instantané, il faut le temps de l'empaqueter, tout de même !), elle est automatiquement disponible pour tous ceux qui ont installé ce paquet.

Installation
------------

En tant que *root*, lancez simplement la commande suivante :

.. code:: shell

    apt-get install pluxml

Une série de questions devrait vous être présentée. Ces questions ont une priorité variable : certaines sont de priorité moyenne (questions avec une valeur par défaut pertinente), d'autres de priorité haute (questions sans valeur par défaut pertinente, en l'occurrence une seule question : le mot de passe administrateur de PluXml). Selon le réglage défini pour l'outil de configuration *debconf*, les questions de priorité moyenne peuvent être omises. Avec certains réglages extrêmes, même les questions de priorité élevée peuvent être omises, ce qui définira un mot de passe vide !

Si vos réglages de *debconf* ont eu pour résultat d'omettre des questions, vous pouvez demander de reconfigurer le paquet :

.. code:: shell

    dpkg-reconfigure pluxml

Si tel est votre cas, il peut être pertinent de modifier de façon permanente les réglages de *debconf*, de façon à ce qu'il cesse d'omettre des questions de priorité moyenne pour les prochains logiciels que vous installerez :

.. code:: shell

    dpkg-reconfigure debconf

Utilisation
-----------

Après l'installation, votre instance de PluXml est disponible à l'adresse http://localhost/pluxml, ou http://SERVEUR/pluxml (remplacer *SERVEUR* par le nom ou l'adresse IP de votre serveur) s'il ne s'agit pas de l'ordinateur sur lequel vous travaillez directement.

Vous pourrez par la suite définir un hôte virtuel par nom à votre guise, en utilisant simplement comme racine */usr/share/pluxml*. Par exemple, avec Apache :

.. code:: apache

    <VirtualHost *:80>
        ServerName blog.example.com
        DocumentRoot /usr/share/pluxml
    </VirtualHost>

De la même façon, vous pourrez définir des règles de réécriture d'URL, mais cela dépasse le cadre de ce guide d'installation.

Détails de l'installation
-------------------------

Contrairement à une installation habituelle, avec le paquet Debian les fichiers de PluXml sont séparés de façon à respecter la `FHS <https://fr.wikipedia.org/wiki/Filesystem_Hierarchy_Standard>`_ :

* les fichiers constituant le code de PluXml sont placés dans */usr/share/pluxml* ;
* les fichiers de configuration sont placés dans */etc/pluxml* ;
* les fichiers de données de PluXml, par exemple la liste des utilisateurs, ou encore les articles, sont placés dans */var/lib/pluxml*.

Les droits de ces fichiers sont adaptés de façon à minimiser les dégâts qui pourraient résulter d'un piratage par exploitation d'une faille de PluXml, de l'interpréteur PHP ou du serveur web :

* les fichiers constituant le code de PluXml sont accessible en lecture seule par le serveur web ;
* les fichiers de configuration sont par défaut accessibles en lecture seule par le serveur web, mais une question de configuration du paquet permet d'autoriser l'écriture de façon à pouvoir utiliser l'interface web de configuration ;
* les fichiers de données sont accessibles en lecture et en écriture par le serveur web.
