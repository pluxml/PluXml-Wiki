Mise à jour de PluXml
=====================

Sauvegarder ses données
-----------------------
Avant une mise à jour de PluXml, il faut par précaution, sauvegarder votre site web. La procédure est la même pour une sauvegarde régulière.

PluXml n’ayant pas de base de données, la sauvegarde est très simple. Tous les fichiers de PluXml sont dans un seul et même dossier, qui correspond à la racine de votre site web.
Il suffit de sauvegarder ce dossier racine, en local sur votre ordinateur, sur une clé USB ou sur un autre support externe.

Ainsi, si votre site se trouve dans le répertoire ``/var/www/PluXml``, il suffit de faire une copie du dossier ``PluXml``.

Si vous souhaitez sauvegarder uniquement les articles, les commentaires, les pages statiques, la configuration du site et des plugins, une copie du répertoire ``/var/www/pluxml/data`` est suffisante.


Lancer la mise à jour
---------------------

.. caution::
     Assurez-vous d’avoir fait une sauvegarde de votre site avant de mettre à jour PluXml (voir `Sauvegarder ses données`_).

Suivre les étapes ci-dessous pour effectuer la mise à jour :

- Télécharger la dernière version de `PluXml <https://www.pluxml.org>`_
- Décompresser l'archive ``pluxml-lastest.zip`` précédemment téléchargée
- Sélectionner tout le contenu de l’archive, sauf les dossiers ``data``, ``plugins`` et ``themes``
- Déposer tout le contenu sélectionné à la racine du site **en écrasant les anciens fichiers**
- Accéder au site via votre navigateur Internet et suivre les instructions pour lancer la mise à jour

.. image:: img/update.jpg
   :align: center