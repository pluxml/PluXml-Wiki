Fichiers de langue
==================
Le paramètre d’entrée ``$default_lang`` du constructeur ``__construct()`` de la classe du plugin
contient la langue par défaut utilisée par PluXml. Il permet de charger le fichier de langue du plugin contenu dans le dossier ``lang``.

Exemple :

.. code:: php

    <?php
        class test extends plxPlugin {
            public function __construct($default_lang) {
                # appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
            }
        }
    ?>

Emplacement des fichiers de langue
----------------------------------

Les fichiers de langue sont stockés dans le dossier ``lang`` du plugin. Les fichiers de langue sont nommés de la façon suivante :

- ``fr.php``
- ``en.php``

Si PluXml est configuré en anglais, le paramètre ``$default_lang`` contient la valeur ``en``. Le fichier ``en.php`` dans le répertoire ``/plugins/test/lang/``
est utilisé. De cette façon, les plugins peuvent être multi-langues.

Structure d’un fichier de langue
--------------------------------

Un fichier de langue est un fichier php qui contient un tableau ``$LANG`` avec des mots clés et les traductions dans la langue désirée.

Exemple :

.. code:: php

    <?php
        $LANG = array(
            'L_TITLE'         => 'Plugin de test',
            'L_DESCRIPTION'   => 'Description du plugin de test'
        );
    ?>

Utilisation d’un fichier de langue
----------------------------------

Le fichier de langue correspondant à langue par défaut de PluXml est, s’il existe,
chargé automatiquement par le moteur de plugin. Pour récupérer et utiliser une traduction
à partir d’un plugin, il faut utiliser l’une des deux instructions suivantes :

Renvoie la traduction de la clé passée en paramètre :

.. code:: php

    $this->getLang(‘<clé de traduction>’);

Affiche la traduction de la clé passée en paramètre :

.. code:: php

    $this->lang(‘<clé de traduction>’);

Exemple :

.. code:: php

    <?php
        class test extends plxPlugin {
            public function __construct($default_lang) {
                # appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # Ajoute le hook
                $this->addHook('ThemeEndHead', 'ThemeEndHead');
            }
            public function ThemeEndHead() {
                echo $this->getLang("L_TITLE");
                $this->getLang("L_DESCRIPTION");
            }
        }
    ?>

Fichier d’aide
--------------
Dans le dossier ``lang`` peut également être présent le fichier d’aide du plugin à afficher en fonction de la langue utilisée dan PluXml.
Les fichiers d’aide sont nommés de la façon suivante : ``<lang>-help.php``.

Exemple : ``fr-help.php``, ``en-help.php``

Ces fichiers ne sont pas obligatoires. Si un fichier correspondant à la langue de PluXml existe,
il sera affiché lors du clic sur le lien ``Aide`` du plugin. Si aucun fichier d’aide n’est présent, le lien ``Aide`` n’est pas visible.

Exemple du contenu d'un fichier aide

.. code:: php

    <?php if(!defined('PLX_ROOT')) exit; ?>
    <h2>Aide</h2>
    <p>Fichier d'aide du plugin test</p>

Un fichier d’aide est un simple fichier avec du contenu au format html.

Lien du menu aide
-----------------
Pour des raisons de sécurité il est recommandé d'ajouter la ligne suivante au début du fichier d'aide.

.. code:: php

    <?php if(!defined('PLX_ROOT')) exit; ?>
