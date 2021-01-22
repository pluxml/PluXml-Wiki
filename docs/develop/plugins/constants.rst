Liste des constantes
====================

PluXml dispose de constante contenant des valeurs prédéfinies et ne pouvant pas être modifiées :

- PLX_ADMIN : Contient la valeur ``true`` si on est dans l’administration de PluXml
- PLX_AUTHPAGE : Contient la valeur ``true`` si on est sur la page d’identification ``core/admin/auth.php``
- PLX_CHARSET : Contient le charset utilisé par PluXml (utf-8 par défaut)
- PLX_CONF : Contient le chemin par defaut du fichier ``parametres.xml`` (``PLX_ROOT.'data/configuration/parametres.xml'``)
- PLX_CONFIG_PATH : Contient le chemin par défaut vers le dossier ``data/configuration/``
- PLX_CORE : Contient l’emplacement du dossier ``core`` (``PLX_ROOT.'core/'``)
- PLX_DEBUG : Contient la valeur ``true`` en phase de développement pour charger ou non les fichiers javascript minimisés de PluXml et afficher les messages d’erreurs détaillés
- PLX_FEED : Contient la valeur ``true`` si on est sur le script ``feed.php``
- PLX_MICROTIME : Contient les données du timer d’exécution des scripts renvoyées par ``getMicrotime()``
- PLX_PLUGINS : Contient l’emplacement du dossier ``plugins`` (``plugins/``)
- PLX_ROOT : Contient le chemin relatif vers la racine du site par rapport au fichier courant (par exemple ./ ou ./../)
- PLX_UPDATE : Contient l’emplacement du dossier de mise à jour (``PLX_ROOT.'update/'``)
- PLX_UPDATER : Contient la valeur ``true`` si on est sur le script de mise à jour de PluXml
- PLX_VERSION : Contient le n° de version de PluXml
