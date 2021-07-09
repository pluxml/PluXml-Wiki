Les commentaires
================

Les commentaires peuvent être modifiés, supprimés ou mis hors ligne, depuis l’interface d’administration de PluXml via le menu Commentaire. L’administrateur peut agir sur les commentaires via deux écrans : *Liste des commentaires* et *Edition d’un commentaire*.

Autoriser ou interdire les commentaires
---------------------------------------
Par défaut, les commentaires postés par les internautes sont publiés automatiquement. Toutefois, l’administrateur du site peut interdire leur publication soit globalement sur l’ensemble du site, soit unitairement par article. À noter la présence d’une option pour modérer un commentaire à sa création.

**Pour tous les articles**

Pour interdire les commentaires, il faut se rendre sur l’interface d’administration de PluXml, puis dans *Paramètres > Configuration de base* :

Sélectionnez *Non* à la ligne *Autoriser les commentaires*. Cliquez sur le bouton *Modifier* la configuration de base pour enregistrer le nouveau réglage.

L’interdiction globale supprime la possibilité de créer un commentaire pour tous les articles du site. Cependant, cette option n’efface pas ceux préalablement publiés.

Pour les autoriser, reprendre la même procédure en sélectionnant *Oui* à la ligne *Autoriser* les
commentaires.

**Pour un article spécifique**

L’autorisation ou l’interdiction de commentaires peuvent être gérées article par article. Pour interdire les commentaires sur un article spécifique, se rendre sur l’interface d’administration de PluXml, puis cliquer sur le menu *Articles*. Éditez l’article (lien Éditer). Sélectionnez *Non* pour le paramètre Autoriser les commentaires. Cliquez sur le bouton *Enregistrer*, *Publier* ou *Enregistrer le brouillon* selon l’état de l’article afin d'enregistrer le nouveau réglage.

Le paramètre *Autoriser les commentaires* n’apparaît pas si les commentaires sont globalement interdits.

Pour autoriser les commentaires sur un article, reprendre la même procédure en sélectionnant *Oui* pour le paramètre Autoriser les commentaires.

**Modérer les commentaires à leur création**

PluXml offre la possibilité de modérer les commentaires à leur création. Cela signifie que chaque commentaire doit être validé par l’administrateur du site pour être publié. Pour activer la modération des commentaires à leur création, il faut se rendre sur l'interface
d'administration de PluXml, menu *Paramètres*, sous-menu *Configuration de base*.

Sélectionnez *Oui* à la ligne *Modérer les commentaires à la création*. Cliquer sur le bouton Modifier la configuration de base afin d'enregistrer le nouveau réglage.

Lorsque la modération des commentaires à leurs créations est activée, chaque commentaire créé, est consultable dans le menu Commentaires de l’interface d’administration de PluXml. Pour le mettre en ligne, lire la section *Commentaires en ligne* ci-dessous.

### Liste des commentaires

Cet écran présente les commentaires sous forme d’un tableau à 4 colonnes :

* Date : date de création du commentaire.
* Message : texte du commentaire accompagné de son statut (en ligne ou hors ligne).
* Auteur : auteur du commentaire.
* Action : actions d'administration disponibles pour ce commentaire
  - Répondre : renvoie vers l'écran de réponse au commentaire.
  - Éditer : modifier le commentaire.
  - Article : renvoie vers l'écran de modification de l’article attaché au commentaire.

.. image:: img/liste-commentaires.jpg
   :align: center

Une liste de choix déroulante Pour la sélection... est accessible en haut de l’interface. L’action choisie dans cette liste sera appliquée à chaque message coché, après un clic sur le bouton Ok. Les actions disponibles sont :

* Mettre en ligne
* Mettre hors ligne
* Supprimer

Deux liens en bas de page permettent de s’abonner aux flux RSS des commentaires hors ligne et en-ligne. Ces deux flux sont privés, ils permettent à l’administrateur de suivre la publication de commentaires sur son site et d’entrer directement dans le menu l’administration de PluXml pour arriver sur l’écran *Édition d’un commentaire*.

Édition d’un commentaire
------------------------

Éditez le commentaire en cliquant sur le lien Éditer, situé à droite du commentaire dans la colonne *Action*. La page *Édition d’un commentaire* s’affiche.

.. image:: img/ecrire-commentaires.jpg
   :align: center

Plusieurs actions sont mises à disposition de l’administrateur via une série de boutons placés en bas de page. Les actions disponibles dépendent du statut du commentaire édité. Actions disponibles pour un commentaire en ligne :

* Suppression
* Mise hors ligne
* Réponse au commentaire
* Mise à jour

Actions disponibles pour un commentaire hors ligne

* Suppression
* Mise en ligne
* Mise à jour

**Commentaires en ligne**

Par défaut, un commentaire créé est au statut *En ligne* (si l’option Modérer les commentaires à la création n’est pas activée). Par conséquent, il sera affiché sur le site en partie publique après l'article concerné.

Pour mettre en ligne un commentaire, il faut agir via l’interface d’administration des commentaires sur l’action Mettre en ligne de l’écran Liste des commentaires ou sur le bouton Valider la publication de l’écran Édition d’un commentaire.

**Commentaires hors ligne**

L’interface d'administration de PluXml permet d’identifier rapidement le nombre de commentaires hors ligne. Le nombre de commentaire
hors ligne est affiché en blanc sur fond rouge à droite du menu *Commentaires*.

.. image:: img/commentaires-horsligne.jpg
   :align: center

Un commentaire est hors ligne s’il a été modéré par l’administrateur ou si la publication dès la création a été désactivée par l’administrateur (option Modérer les commentaires à la création activée).

Pour mettre hors ligne un commentaire, il faut agir via l’interface d’administration des commentaires sur l’action Mettre hors en ligne
de l’écran Liste des commentaires ou sur le bouton Mettre hors ligne de l’écran Édition d’un commentaire.

**Modifier un commentaires**

Tout commentaire peut être modifié, qu’il soit en ligne ou hors ligne, via l’écran Edition d’un commentaire. Ce dernier permet la modification des champs Date et heure de publication, Auteur, Site, E-mail et Commentaire (le contenu du message).

Pour un commentaire en ligne, toute modification apportée à l’un de ces champs sera publiée en cliquant sur le bouton Mettre à jour. Le texte est au format html, c’est-à-dire que si vous souhaitez le mettre en forme, vous pourrez utiliser les balises du langage html. Si vous n'êtes pas familier avec le langage html, il existe plusieurs plugins qui vous permettront d'enrichir ces formulaires avec un éditeur WYSIWYG.

.. note::

    Voir la section : :doc:`Plugins </docs/customize/plugins>`

Pour un commentaire hors ligne, la modification apportée sera enregistrée en cliquant sur le bouton *Mettre à jour*. Vous pouvez enregistrer et publier le commentaire en même temps en cliquant sur le bouton Valider la publication.

Répondre à un commentaire
-------------------------

L’administrateur peut répondre à un commentaire en cliquant sur le lien Répondre, depuis l’écran Liste des commentaires ou en cliquant sur Répondre à ce commentaire depuis l’écran *Édition d’un commentaire*.

.. image:: img/repondre-commentaire.jpg
   :align: center

Cette page est divisée en deux parties :

* Rédiger un commentaire : l e champ Informations permet de répondre. Le code HTML déjà présent affiche la date et le nom de l’auteur du commentaire à qui on répond.
* Commentaires de cet article : affichage ante-chronologique des commentaires attachés à l’article.

Pour répondre, saisir du texte dans le champ Informations puis cliquez sur le bouton Enregistrer. La réponse est alors immédiatement publiée. Le texte est au format html, c’est-à-dire que si vous souhaitez le mettre en forme, vous pourrez utiliser les balises du langage html. Si vous n’êtes pas familier avec le langage HTML, il existe plusieurs plugins qui vous permettront d’enrichir ces formulaires avec un éditeur WYSIWYG.

.. note::

    Voir la section : :doc:`Plugins </docs/customize/plugins>`

Supprimer un commentaire
------------------------

Tout commentaire peut être supprimé, qu’il soit en ligne ou hors ligne, via les deux écrans d’administration des commentaires (Liste des commentaires et Édition d’un commentaire).

Liste des commentaires :

* Cocher le commentaire à supprimer.
* Sélectionner l’action *Supprimer* dans la liste déroulante *Pour la sélection...*
* Cliquer sur le bouton *Ok*

Le commentaire est immédiatement supprimé, sans demande de confirmation.

Édition d’un commentaire :

* Cliquer sur le bouton *Supprimer*.
* Une fenêtre demande la confirmation de suppression
* Cliquer sur *Ok* pour supprimer définitivement le commentaire.

Flux RSS des commentaires
-------------------------

Accessibles depuis l’administration à l’écran Liste des commentaires, ces flux RSS, permettent aux utilisateurs du site, de suivre la publication de nouveaux commentaires.

Les utilisateurs ayant les droits suffisants peuvent accéder directement depuis ces flux, aux écrans de modérations des commentaires, grâce à un lien présent dans le flux RSS.
