Créer un écran de configuration
===============================
Il est possible d’avoir un écran de configuration réservé à un ou plusieurs profils d'utilisateur définis par le programmeur,
afin de renseigner des paramètres nécessaires au fonctionnement du plugin.
Cet écran est conçu par le développeur du plugin en fonction de ses besoins et de celui du plugin.

Création de l'écran de configuration
------------------------------------
Le fichier correspondant à l’écran de configuration s’appelle ``config.php``.
Il est stocké dans le dossier du plugin. Il n’est pas obligatoire. Si ce fichier est présent,
il sera accessible en cliquant sur le lien *Configuration* du plugin dans l’écran de *Gestion des plugins* (Menu Paramètres > Sous-menu Plugins).

.. image:: img/admin-param-plugins.jpg
   :align: center

On accède alors au fichier parametres_plugin.php grâce l’url ``parametres_plugin.php?p=test``
(où la valeur du paramètre *p* est le nom du plugin).

Lors du chargement du fichier ``parametres_plugin.php`` le fichier ``config.php`` du plugin demandé est chargé et affiché à l’écran.

Exemple de contenu du fichier ``config.php`` :

.. code:: php

    <?php if(!defined('PLX_ROOT')) exit; ?>
    <?php
        # Control du token du formulaire
        plxToken::validateFormToken($_POST);
        if(!empty($_POST)) {
            $plxPlugin->setParam('param1', $_POST['param1'], 'numeric');
            $plxPlugin->setParam('param2', $_POST['param2'], 'string');
            $plxPlugin->setParam('param3', $_POST['param3'], 'cdata');
            $plxPlugin->saveParams();
            header('Location: parametres_plugin.php?p=test');
            exit;
        }
    ?>
    <form class="inline-form" action="parametres_plugin.php?p=test" method="post" id="form_test">
        <fieldset>
            <p>
                <label for="id_param1">Paramètre 1 :</label>
                <?php plxUtils::printInput('param1',$plxPlugin->getParam('param1'),'text','4-4') ?>
            </p>
            <p>
                <label for="id_param2">Paramètre 2 :</label>
                <?php plxUtils::printInput('param2',$plxPlugin->getParam('param2'),'text','20-20') ?>
            </p>
            <p>
                <label for="id_param3">Paramètre 3 :</label>
                <?php plxUtils::printInput('param3',$plxPlugin->getParam('param3'),'text','20-20') ?>
            </p>
            <p class="in-action-bar">
                <?php echo plxToken::getTokenPostMethod() ?>
                <input type="submit" name="submit" value="Enregistrer" />
            </p>
        </fieldset>
    </form>

La première ligne du fichier est indispensable car elle apporte une sécurité au plugin mais aussi à tout PluXml
en interdisant d’appeler et d’exécuter directement le fichier ``config.php`` sans passer par PluXml.

.. code:: php

    <?php if(!defined('PLX_ROOT')) exit; ?>

Formulaire de saisie
--------------------

Le formulaire de saisie servant à renseigner les différents paramètres qui seront sauvegardés
dans le fichier ``parametres.xml`` doit être déclaré de la façon suivante :

.. code:: html

    <form action="parametres_plugin.php?p=test" method="post">
        ...
    </form>

L’argument action de la balise ``<form>`` doit pointer vers l’url ``parametres_plugin.php?p=test``
où la valeur du paramètre *p* est le nom du plugin (équivalent au nom du dossier du plugin).

Ajouter un bouton dans la barre d’action
----------------------------------------

Pour ajouter un bouton d’action dans la barre d’action, déclarer le dans une balise ``<p>`` ayant la classe CSS : ``in-action-bar``.
De cette façon le bouton sera automatiquement positionné dans la barre d’action.

.. code:: html

    <p class="in-action-bar">
        <?php echo plxToken::getTokenPostMethod() ?>
        <input type="submit" name="submit" value="Enregistrer" />
    </p>

Sécurité
--------
La ligne suivante est obligatoire. Elle créer un champ caché contenant un code de sécurité (CSRF token)
qui sera vérifié lors du traitement des données du formulaire.

.. code:: php

    <?php echo plxToken::getTokenPostMethod() ?>

Les lignes suivantes sont obligatoires. Elles permettent de vérifier le code de sécurité contenu
dans le champs caché et créé par ``plxToken::getTokenPostMethod()``

.. code:: php

    <?php plxToken::validateFormToken($_POST); ?>

Définir les droits d’accès
--------------------------
Les droits d’accès à l’écran de configuration se définissent dans le code du plugin, grâce à l’instruction :

.. code:: php

    <?php $this->setConfigProfil(<profil>); ?>

Les profils disponibles sont définis par les constantes :

- PROFIL_ADMIN : administrateur
- PROFIL_MANAGER : gestionnaire
- PROFIL_MODERATOR : modérateur
- PROFIL_EDITOR : éditeur
- PROFIL_WRITER : rédacteur

Plusieurs profils peuvent être spécifiés en les séparant par des virgules :

.. code:: php

    <?php $this-> setConfigProfil(PROFIL_ADMIN, PROFIL_WRITER); ?>

Exemple :

.. code:: php

    <?php
        class test extends plxPlugin {
            public function __construct($default_lang) {
                # appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # limite l'accès à l'écran d'administration du plugin
                $this->setConfigProfil(PROFIL_ADMIN);
            }
        }
    ?>

Si les droits autorisant l’accès à l’écran ``config.php`` ne sont pas précisés ou non valides,
l’utilisateur sera redirigé vers la page ``index.php`` de l’administration avec un message d’erreur « *Accès interdit* ».
