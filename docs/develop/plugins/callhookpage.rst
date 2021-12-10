Appeler un hook à partir d’une page statique
============================================

Il est tout a fait possible d’appeler un hook à partir d’une page statique.

Exemple :

.. code:: php

    <?php
        global $plxShow;
        eval($plxShow->callHook('Static1Test'));
    ?>

Il faut dans un premier temps déclarer ``$plxShow`` en tant que variable globale.

.. code:: php

    global $plxShow;

Pour appeler un hook, nous utilisons la fonction ``callHook`` de ``$plxShow``
en passant en paramètre le nom du hook à traiter. Le passage de paramètres et valeur de retour sont autorisés.
