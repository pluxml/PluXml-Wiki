Le squelette d’un plugin
========================

Les plugins de PluXml sont installés dans le dossier ``/plugins``. Chaque dossier des plugins doit respecter un nommage simple :
pas d'espace, pas de caractères spéciaux et accentués. La constante `PLX_PLUGINS` permet de connaître le dossier de stockage des plugins.

Contenu du dossier d’un plugin
------------------------------

Un plugin est composé de plusieurs fichiers : certains sont obligatoires, d’autres optionnels.

.. list-table::
   :widths: 15 85
   :header-rows: 1

   * - Nom du fichier
     - Description
   * - ``admin.php``
     - Fichier utilisé dans l’administration de PluXml. Contient l’interface pour les utilisateurs accédant à l’administration de PluXml pour utiliser le plugin
   * - ``config.php``
     - Fichier utilisé dans l’administration de PluXml. Contient l’interface pour les administrateurs pour configurer et paramétrer le plugin
   * - ``icon.png``
     - Image identifiant le plugin et affichée sur l’écran de gestion des plugins (Menu Paramètres > Plugins). Formats autorisés : jpg, gif, png. Taille de l’image : 48 x 48 pixels
   * - ``infos.xml``
     - **Obligatoire** - Fichier xml contenant les informations sur le plugin : Titre, Auteur, N° de version, Date du plugin, Site de l’auteur, Description du plugin, Scope
   * - ``parameters.xml``
     - Fichier xml contenant le paramétrage servant au fonctionnement du plugin. Depuis la version 5.1.7 de PluXml, le fichier parameters.xml est stocké dans le dossier \\data/configuration/plugins/\\
   * - ``plugin.php``
     - **Obligatoire** - Fichier core du plugin. Le nom du fichier doit être le même que celui du répertoire dans lequel il est stocké, écrit avec la même orthographe en respectant les majuscules et minuscules.

Les fichiers composants un plugin
---------------------------------

Développer un plugin nécessite de coder le fichier plugin.php en respectant un squelette et en utilisant diverses fonctions mises à disposition du développeur afin d’interagir avec PluXml et ses utilisateurs.

Prenons l’exemple d’un plugin test composé du fichier test.php

.. code:: php

    <?php
      class test extends plxPlugin {
        public function __construct($default_lang) {
          # appel du constructeur de la classe plxPlugin (obligatoire)
          parent::__construct($default_lang);
        }
      }
    ?>

Un plugin est une classe portant le même nom que le dossier dans lequel il est stocké. Cette classe est dérivée
de la classe ``plxPlugin`` propre à PluXml et au fonctionnement des plugins.

.. caution::

     Le nom de la classe doit être identique au nom du dossier du plugin : même orthographe en respectant les majuscules et les minuscules.

Si le plugin est stocké dans un dossier s’appelant test, la classe du plugin devra porter également le nom test.

.. code:: php

    <?php
      class test extends plxPlugin
      {
        [...]
      }
    ?>

Le constructeur de la classe ``test`` ainsi que l'appel au constructeur de la classe parente sont obligatoire.

.. code:: php

    <?php
      class test extends plxPlugin
      {
        public function __construct($default_lang) {
          # appel du constructeur de la classe plxPlugin (obligatoire)
          parent::__construct($default_lang);
        }
      }
    ?>

Le paramètre ``$default_lang`` contient la langue par défaut utilisée par PluXml. Il servira à charger le fichier de langue du plugin s’il existe.
