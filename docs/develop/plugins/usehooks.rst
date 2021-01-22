Modifier le comportement de PluXml
==================================

Injecter du code
----------------
Voyons maintenant comment modifier le comportement d'une fonction de PluXml.
Nous allons prendre comme exemple, l'ajout d'un champ de saisie sur l'écran de gestion des options des catégories. Pour cela il nous faut :

- rajouter un champ de saisie sur l'écran des options des catégories (Menu Catégories > Liens Options)
- enregistrer la valeur saisie lors du clic sur le bouton dans le fichier ``data/configuration/categories.xml``
- lire la nouvelle donnée lorsque le fichier ``data/configuration/categories.xml`` est chargé

.. image:: img/plugin-exemple.jpg
   :align: center

Liste des hooks utilisés :
--------------------------

.. list-table::
   :widths: 25 25 20 30
   :header-rows: 1

   * - Hook
     - Fichier
     - Méthode
     - Emplacement
   * - ``plxAdminEditCategoriesNew``
     - ``class.plx.admin.php``
     - ``editCategories()``
     - New : création
   * - ``plxAdminEditCategoriesUpdate``
     - ``class.plx.admin.php``
     - ``editCategories()``
     - Update : mise à jour
   * - ``plxAdminEditCategoriesXml``
     - ``class.plx.admin.php``
     - ``editCategories()``
     - XML : mise en forme XML
   * - ``plxAdminEditCategorie``
     - ``class.plx.admin.php``
     - ``editCategories()``
     - Lecture des données XML dans le fichier ``categories.xml``
   * - ``AdminCategory``
     - ``categorie.php``
     -
     - Ecran gérant les options d'une catégorie
   * - ``plxMotorGetCategories``
     - ``class.plx.motor.php``
     - ``getCategories()``
     - Lecture des données XML dans le fichier ``categories.xml``

Code du plugin
--------------

.. code:: php

    <?php
        class categories extends plxPlugin {
            public function __construct($default_lang) {
                # appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # Ajoute des hooks
                $this->addHook('plxAdminEditCategoriesNew', 'plxAdminEditCategoriesNew');
                $this->addHook('plxAdminEditCategoriesUpdate', 'plxAdminEditCategoriesUpdate');
                $this->addHook('plxAdminEditCategoriesXml', 'plxAdminEditCategoriesXml');
                $this->addHook('plxMotorGetCategories', 'plxMotorGetCategories');
                $this->addHook('plxAdminEditCategory', 'plxAdminEditCategory');
                $this->addHook('AdminCategory', 'AdminCategory');
            }
            public function plxAdminEditCategoriesNew() {
                echo "<?php \$this->aCats[\$content['new_catid']]['test']=''; ?>";
            }
            public function plxAdminEditCategoriesUpdate() {
                echo "<?php \$this->aCats[\$cat_id]['test']=(isset(\$this->aCats[\$cat_id]['test'])?\$this->aCats[\$cat_id]['test']:'')?>";
            }
            public function plxAdminEditCategoriesXml() {
                echo "<?php \$xml .= '<test><![CDATA['.plxUtils::cdataCheck(\$cat['test']).']]></test>'; ?>";
            }
            public function plxMotorGetCategories() {
                echo "<?php \$this->aCats[\$number]['test'] = isset(\$iTags['test'][\$i])?\$values[\$iTags['test'][\$i]]['value']:'';?>";
            }
            public function plxAdminEditCategory() {
                echo "<?php \$this->aCats[\$content['id']]['test'] = trim(\$content['test']); ?>";
            }
            public function AdminCategory() {
                $string = <<<END
                <?php
                    echo '<p class="field"><label for="id_test">Test&nbsp;:</label></p>';
                    plxUtils::printInput('test', plxUtils::strCheck(\$plxAdmin->aCats[\$id]['test']),'text', '10-255');
                ?>
                END;
                echo $string;
            }
        }
    ?>

Détail du code
--------------

.. code:: php

    public function AdminCategory () {
        $string = <<<END
            <?php
              echo '<p class="field"><label for="id_test">Test&nbsp;:</label></p>';
              plxUtils::printInput('test', plxUtils::strCheck(\$plxAdmin->aCats[\$id]['test']), 'text', '10-255');
            ?>
        END;
        echo $string;
    }

La méthode ``AdminCategory()`` permet d'afficher le nouveau champ sur l'écran des options de la catégorie “Rubrique 1”.

La chaîne de caractère ``$string`` contient le code qui va être interprété lorsque la page options sera chargée.
C'est pour cette raison qu'il est nécessaire de préciser les balises ``php`` au début et à la fin de ``$string``.

Notez l'alternative pour renseigner ``$string`` grâce à ``END ... END;``.
Notez également l'utilisation du caractère \\ devant chaque variable comme par exemple devant ``$plxAdmin->aCats``
car ici il ne s'agit non pas d'une variable locale à la méthode ``AdminCategory()``,
mais d'une variable utilisée dans le fichier `categorie.php`.

.. code:: php

    public function plxAdminEditCategoriesNew () {
        echo "<?php \$this->aCats[\$content['new_catid']]['test']=''; ?>";
    }

La méthode ``plxAdminEditCategoriesNew()`` injecte le code php devant être utilisé dans la fonction
servant à renseigner le tableau ``$this->aCats``. Encore une fois, nous utilisons les balises php car le code
ne doit pas simplement être affiché, mais interprété par la fonction qui utilise le hook ``plxAdminEditCategoriesNew``.

De façon plus générale, nous déclarons le code tel qu’il serait écrit si nous modifions directement
le code de la fonction ``editCategories`` du fichier ``class.plx.admin.php``.

Il ne reste plus qu'à écrire tout le code nécessaire pour gérer le nouveau champ *test* comme par exemple la méthode ``plxAdminEditCategoriesXml()``
qui formate la chaîne XML sauvegardée dans le fichier ``categories.xml`` dans le fichier ``class.plx.admin.php`` méthode ``editCategories()``.

Interrompre une fonction de PluXml
----------------------------------
Certains hooks acceptent de recevoir en retour de traitement une valeur afin d’interrompre l’exécution
de la fonction appelante. Dans le code d'un plugin, pour arrêter l’exécution de la fonction de PluXml "hookée", il faut utiliser la syntaxe :

.. code:: php

    return true;

Un simple ``return;`` ne fonctionne pas, ceci est du à l'utilisation de la fonction ``eval`` servant à évaluer le code du plugin.
Pour éviter que le code suivant l’instruction ``eval`` ne soit exécuté, il faut donc faire apparaître dans le plugin :

.. code:: php

    return true;

Exemple :

.. code:: php

    public function plxMotorDemarrageBegin(){
        $string = <<<END
            <?php
                if(\$this->mode=="galerie"){
                    \$this->template = 'galerie.php';
                    return true;
                }
            ?>
            END;
        echo $string;
    }

Ici on injecte du code comme si on l'avait saisi au début de la méthode ``Demarrage()`` de la classe ``plxMotor``.
Si la condition du ``if`` est valide, on fait un ``return true;`` pour arrêter la suite du code de la méthode
``Demarrage()``. Au niveau de la syntaxe, si un simple ``return;`` était utilisé, la suite du code serait quand même exécutée.
Il faut donc bien mettre ``return true;``

Tous les hooks n’acceptent pas de valeur de retour (voir tableau des hooks). En effet un hook qui est en fin
d'une fonction de PluXml, n'a aucun intérêt à gérer une valeur de retour sur un ``return``. Par exemple dans le fichier ``class.plx.show.php`` :

.. code:: php

    public function pageTitle() {
        # Hook Plugins
        if(eval($this->plxMotor->plxPlugins->callHook('plxShowPageTitle'))) return;
        ...
    }

Ici le hook est au début de la méthode ``pageTitle()``. Il peut donc être utile de ne pas exécuter la suite du code.
On a donc une syntaxe avec un ``if`` qui va tester la valeur de retour envoyée par le plugin grâce à la ligne :
``return true;``. Autre exemple dans ``class.plx.admin.php`` :

.. code:: php

    public function __construct($filename) {
        parent::__construct($filename);
        # Hook plugins
        eval($this->plxPlugins->callHook('plxAdminConstruct'));
    }

Ici le hook est à la fin du constructeur de la class ``plxAdmin``. Il n’y a plus de code après.
Il est donc inutile de gérer une valeur de retour passée par ``return true;`` pour interrompre le code. Un appel à l’instruction if est gagné.
