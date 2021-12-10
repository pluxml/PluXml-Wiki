Utiliser les hooks prédéfinis pour les thèmes
=============================================

Il existe deux hooks prédéfinis pour être utilisés dans les thèmes : ``ThemeEndHead`` et ``ThemeEndBodyHook``

ThemeEndHead
------------

Le hook ``ThemeEndHead`` permet d’injecter du code dans la balise ``head`` dans la page
du site coté visiteurs. Voilà un exemple qui ajoute dans la balise ``head`` l’appel
du fichier javascript ``fichier.js`` :

.. code:: php

    <?php
        class test extends plxPlugin {
            public function __construct($default_lang) {
                # appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # déclaration du hook
                $this->addHook('ThemeEndHead', 'ThemeEndHead');
            }
            public function ThemeEndHead() {?>
                <script type="text/javascript" src="fichier.js"></script>
                <?php
            }
        }
    ?>


Hook ThemeEndBody
-----------------

Le hook ``ThemeEndBody`` permet d’injecter du code dans la balise body dans la page du site coté visiteurs.
Voilà un exemple qui ajoute dans la balise du code javascript :

.. code:: php

    <?php
        class test extends plxPlugin {
            public function __construct($default_lang) {
                # appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # déclaration du hook
                $this->addHook('ThemeEndHead', 'ThemeEndHead');
            }
            public function ThemeEndHead() {?>
                <script type="text/javascript">
                    <!—-
                    function myfunction(text) {
                    alert(text);
                    }
                    -->
                </script>
                <?php
            }
        }
    ?>
