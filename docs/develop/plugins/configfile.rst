Fichier parameters.xml
======================
Le fichier ``parameters.xml`` contient les données utilisées comme paramètres pour le fonctionnement du plugin.
Les fichiers ``parameters.xml`` des plugins sont stockés dans le dossier ``data/configuration/plugins/``.

Structure du fichier
--------------------

Exemple :

.. code:: xml

    <?xml version='1.0' encoding='UTF-8'?>
    <document>
        <parameter name="param1" type="numeric">999</parameter>
        <parameter name="param2" type="string">parametre</parameter>
        <parameter name="param3" type="cdata"><![CDATA[parametre 2]]></parameter>
    </document>

Chaque paramètre est à mettre dans une balise ``parameter``. Les attributs ``name`` et ``type`` sont obligatoires.
Un type peut être ``numeric``, ``string`` ou ``cdata``. Il conditionne la façon de stocker le contenu de la balise ``parameter``.
Le nom des paramètres est libre.

.. code:: xml

    <parameter name="param1" type="numeric">999</parameter>
    <parameter name="titre" type="string">titre</parameter>

Le fichier ``parameters.xml`` peut être utilisé et renseigné de plusieurs façons :

- renseigné et utilisé à partir du code du plugin,
- renseigné de manière interactive à partir de l’écran de configuration du plugin.

Lecture des données du fichier ``parameters.xml``
-------------------------------------------------
La méthode ``getParam`` de l’object ``$plxPlugin`` permet de récupérer la valeur d’un paramètre stocké dans le fichier ``parameters.xml``.

Exemple :

.. code:: php

    $plxPlugin->getParam('param1')

Écriture des données dans le fichier ``parameters.xml``
-------------------------------------------------------
L’écriture se fait en 2 temps :

- renseigner la valeur du paramètre en appelant la méthode ``setParam`` de l’object ``$plxPlugin``
- sauvegarder les données dans le fichier en appelant la méthode ``saveParams`` de l’object ``$plxPlugin``

Définir un paramètre
--------------------

.. code:: php

    $plxPlugin->setParam(‘<nom du parametre>‘, ‘<valeur du parameter>’, ‘<type du parametre>’)

``setParam`` permet de définir la valeur d’un paramètre.

Le type de paramètre doit être une valeur parmi ``numeric``, ``string``, ``cdata``

Exemple :

.. code:: php

    $plxPlugin-> setParam ('param1', 12345, 'numeric')

Sauvegarder les paramètres
--------------------------

``saveParams`` permet de sauvegarder tous les paramètres dans le fichier ``parametres.xml`` du plugin.

Exemple :

.. code:: php

    $plxPlugin->saveParams()

Voici un exemple de code qui affiche un formulaire en pré-renseignant les zones de saisies à partir
des données stockées dans le fichier ``parameters.xml``, puis qui sauvegarde les nouvelles valeurs saisies une fois le formulaire soumis.

Exemple :

.. code:: php

    <?php
        if(!empty($_POST)) {
            $plxPlugin->setParam('param1', $_POST['param1'], 'numeric');
            $plxPlugin->setParam('param2', $_POST['param2'], 'string');
            $plxPlugin->setParam('param3', $_POST['param3'], 'cdata');
            $plxPlugin->saveParams();
        }
    ?>
    <form action="parametres_plugin.php?p=test" method="post">
        Parametre 1 : <input type="text" name="param1" value="<?= plxUtils::strCheck($plxPlugin->getParam('param1')) ?>"/><br>
        Parametre 2 : <input type="text" name="param2" value="<?= plxUtils::strCheck($plxPlugin->getParam('param2')) ?>"/><br>
        Parametre 3 : <input type="text" name="param3" value="<?= plxUtils::strCheck($plxPlugin->getParam('param3')) ?>"/><br>
        <br>
        <input type="submit" name="submit" value="Enregistrer" />
    </form>

Il est indispensable d’utiliser la fonction ``plxUtils::strCheck`` afin de protéger l’affichage des caractères
spéciaux mais aussi pour éviter, par exemple, d’injecter du code javascript (failles XSS).
