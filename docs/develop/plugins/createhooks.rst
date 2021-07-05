Créer ses propres hooks
=======================

Hooks utilisateur
-----------------

Il est possible de définir ses propres noms de hooks et de les appeler dans les thèmes.
Nous connaissons déjà la liste des hooks réservés au fonctionnement de PluXml,
mais il est tout à fait possible de définir ses propres hooks.

Voyons le cas suivant : nous souhaitons définir un hook qui agira dans le fichier ``sidebar.php``
du dossier ``theme``. Nous appellerons ce hook ``SidebarTest`` afin de respecter la nomenclature des noms des hooks.

Commençons par écrire notre plugin :

.. code::php

    <?php
        class test extends plxPlugin {
            public $var='Hook de la sidebar';
            public function __construct($default_lang) {
                # appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # déclaration du hook
                $this->addHook('SidebarTest', 'SidebarTest');
            }
            public function SidebarTest() {
                echo $this->var;
            }
        }
    ?>

Nous retrouvons ici tous les composants décris dans les paragraphes précédents.
Il s’agit ici d’afficher uniquement le message "Hook de la sidebar", message définit dans la variable $var.

Modifions maintenant le fichier ``sidebar.php`` du thème afin de placer l’appel de notre hook.

.. code:: php

    <?php if(!defined('PLX_ROOT')) exit; ?>
    <div id="sidebar">
        ...
    <?php eval($plxShow->callHook('SidebarTest')) ?>
    </div>

Nous utilisons ici la fonction ``callHook`` de ``$plxShow`` en passant en paramètre le nom du hook à traiter.

Passage de paramètres à un hook
-------------------------------

Un hook peut être appelé en lui passant un ou plusieurs paramètres.

Exemple :

.. code:: php

    <?php eval($plxShow->callHook('MyHook', 'param1')) ?>

Pour appeler un hook avec plusieurs paramètres, il faut les passer sous forme de tableau.

..code:: php

    <?php eval($plxShow->callHook('MyHook', array('param1', 'param2'))) ?>

Déclaration du hook recevant les paramètres
-------------------------------------------

Soit le hook ``MyHook`` appelé avec 2 paramètres valant chacun ``azerty`` et ``qwerty`` :

.. code:: php

    <?php eval($plxShow->callHook('MyHook', array('azerty', 'qwerty'))) ?>
    <?php
        class test extends MyPlugin {
            public function __construct($default_lang) {
                # Appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # Déclaration des hooks
                $this->addHook('MyHook', 'MyHookFunction');
            }
            public function MyHookFunction($params) {
                echo $param[0];
                echo $param[1];
            }
        }
    ?>

Lorsque le hook ``MyHook`` est appelé, la fonction ``MyHookFunction`` est exécutée.
Le paramètre ``$params`` de la fonction ``MyHookFunction`` reçoit les deux paramètres
sous forme de tableau. Ainsi ``$params[0]`` contient la valeur ``azerty`` et ``$param[1]`` la valeur ``qwerty``

Le hook MyHook affiche :

    azerty
    qwerty

Valeur de retour d'un hook
--------------------------

Un hook peut retourner une valeur à la page appelante.

Exemple :

.. code:: php

    <?php
        $retour = $plxShow->callHook('MyHook');
        echo $retour;
    ?>

.. attention::

    L'appel d'un hook renvoyant une valeur ne doit pas être fait avec la fonction eval.

La syntaxe suivante ne doit pas être utilisée :

.. code:: php

    <?php $retour = eval($plxShow->callHook('MyHook')) ?>

Il est possible de combiner valeur de retour et passage de paramètres.


.. code:: php

    <?php $retour = $plxShow->callHook('MyHook', 'azerty') ?>

Exemple :

.. code:: php

    <?php
        class test extends MyPlugin {
            public function __construct($default_lang) {
                # Appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # Déclaration des hooks
                $this->addHook('MyHook', 'MyHookFunction');
            }
            public function MyHookFunction() {
                return 'Brian is in the kitchen :)';
            }
    ?>

La phrase ``Brian is in the kitchen :)`` est renvoyée à la page appelante.
L'instruction ``echo $retour;`` affichera cette phrase.
