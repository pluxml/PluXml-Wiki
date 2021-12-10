Comprendre le nom des fichiers xml des articles
===============================================

PluXml n’utilise pas de base de données. Le contenu des articles est stocké dans des fichiers xml.
Si vous utilisez la configuration par défaut, ces fichiers sont enregistrés dans le dossier ``data/articles/``.
Chaque nom de fichier est composé de certaines informations propre à l’article.

Exemple :

.. code::

  _0001.002.001.201304251142.premier-article.xml

Si nous détaillons le nom du fichier, nous avons:

- ``_`` est un caractère optionnel. Il indique que l'article est en attente de validation.
- ``0001`` est l'identifiant de l'article. Il peut aller jusqu'à 9999, donc 9999 articles.
- ``002`` contient l'identifiant de la catégorie dans laquelle l'article est classé. Il peut avoir plusieurs identifiants séparés par des virgules (exemple 001,002). Ici l'article est donc classé dans la catégorie 002. Il n'y a pas de limite dans le nombre de catégories possibles, du moment qu'elles sont bien séparées par des virgules. Il est possible d'avoir également la valeur ``draft`` qui indique que l'article est un brouillon, ou la valeur ``home`` qui indique que l'article est publié dans la catégorie ``Page d'accueil``. Il est donc tout a fait possible d'avoir ``0001.001,002,draft.001.201304251142.premier-article.xml`` 
- ``001`` est l'identifiant de l'utilisateur qui a rédigé l'article.
- ``201304251142`` est la date de publication de l'article. Cela peut être une date future. Cette date est de la forme ``AAAAMMJJHHMM`` où:
  - AAAA = année
  - MM = mois
  - JJ = jour
  - HH = heure
  - MM = minute
- ``premier-article`` est l'url de l'article. On la retrouve dans : ``http://mondomaine.com/index.php?article1/premier-article``
- ``xml`` est l'extension du fichier
