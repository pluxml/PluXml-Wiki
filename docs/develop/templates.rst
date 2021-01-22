Créer un template
=================

Pour créer un template, éditez un nouveau fichier php dans le dossier de votre thème Le nom d'un template est normalisé :

* Template pour la page d'accueil : ``home-xxx.php``
* Template pour un article : ``article-xxx.php``
* Template pour une categorie : ``categorie-xxx.php``
* Template pour une page statique : ``static-xxx.php``

Un fichier template doit toujours commencer par ``home-``, ``article-``, ``categorie-`` ou ``static-`` et se terminer par l'extension ``.php``.
Remplacez *xxxx* par le texte de votre choix pour identifier facilement vos templates.
Pour créer facilement un template vous pouvez dupliquer les fichiers correspondants ``home.php``, ``article.php``,
``categorie.php`` ou ``static.php`` en leur donnant un nom respectant les normes de nommage mentionnées précédemment.

La fonction templateCss()
-------------------------

Cette fonction permet de charger automatiquement un fichier .css spécifique à votre template. Vous  pouvez ainsi donner un style
différent à votre thème dès que le template est appelé. Le fichier ``.css`` associé à un template doit être stocké dans le dossier
thème de votre PluXml et porter le même nom que le template, mais avec l'extension ``.css``. Ainsi si votre template s’appelle
``static-exemple.php`` votre fichier ``.css`` devra s’appeler ``static-exemple.css``.

Assurez-vous que le code ci-dessous existe entre les balises ``<head> ... </head>`` de votre fichier ``header.php``. C'est cette instruction qui permet de charger automatiquement le fichier .css associé à un template, lorsque celui-ci est utilisé.

.. code:: none

    <?php $plxShow->templaceCss(); ?>