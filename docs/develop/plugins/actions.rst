Activation, désactivation et mise à jour d'un plugin
====================================================

Code à exécuter à l’activation d’un plugin
------------------------------------------

Lors de l’activation d’un plugin il est possible d’exécuter du code spécifique. Si la méthode ``OnActivate``
existe dans la classe du plugin, elle sera appelée lors de l’activation du plugin. Cette méthode n’est pas obligatoire.

.. code:: php

    <?php
        class test extends plxPlugin {
            public function __construct($default_lang) {
                # appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
            }
            public function OnActivate() {
                # code à exécuter à l’activation du plugin
            }
        }
    ?>

Code à exécuter à la désactivation d’un plugin
----------------------------------------------

Lors de la désactivation d’un plugin il est possible d’exécuter du code spécifique. Si la méthode ``OnDeactivate``
existe dans la classe du plugin, elle sera appelée lors de la désactivation du plugin. Cette méthode n’est pas obligatoire.

.. code:: php

    <?php
        class test extends plxPlugin {
            public function __construct($default_lang) {
                # appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
            }
            public function OnDeactivate() {
                # code à exécuter à la désactivation du plugin
            }
        }
    ?>

Code à exécuter à la mise à jour d’un plugin
--------------------------------------------

Pour exécuter du code spécifique lors de l’installation d’une nouvelle version d’un plugin, placez dans le dossier
du plugin un fichier texte ``update`` (exemple : ``/plugins/monplugin/update``) contenant la ligne ci-dessous :

.. code:: php

    <?php exit; ?>

Dans le fichier principal du plugin créez une méthode ``onUpdate``. Cette méthode sera exécutée par le moteur des plugins
de PluXml si la présence d’un fichier update est détectée.

Une fois la méthode ``onUpdate`` exécutée, le fichier update est supprimé (pour éviter que ``onUpdate`` soit exécutée à chaque chargement du plugin)

.. code:: php

    <?php
        class test extends plxPlugin {
            public function __construct($default_lang) {
                # appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
            }
            public function OnUpdate() {
                # code à exécuter à la mise à jour du plugin
            }
        }
    ?>
