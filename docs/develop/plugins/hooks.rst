Les hooks
=========

Qu'est-ce qu'un hook ?
----------------------

Le moteur de plugin de PluXml repose sur un système de hooks (« crochets » en français) permettant d’injecter du code php, html, javascript dans celui de PluXml.

Ces parties sont identifiables dans le code de PluXml par l'appel de la méthode *callHook*.

**Exemple 1 : dans les fichiers core**

.. code:: php

    <?php
      eval($this->plxPlugins->callHook('plxMotorConstruct'));
    ?>

**Exemple 2 : dans les fichiers core**

.. code:: php

    <?php
      if(eval($this->plxMotor->plxPlugins->callHook('plxShowPagination'))) return;
    ?>

**Exemple 3 : dans les fichiers de l'administration**

.. code:: php

    <?php
      eval($plxAdmin->plxPlugins->callHook('AdminTopEndHead'))
    ?>

**Exemple 4 : dans les fichiers thèmes**

.. code:: php

    <?php
      eval($plxShow->callHook('PluginTest')))
    ?>

Utilisation des hooks
---------------------

C’est donc la méthode callHook de la classe plxPlugins (fichier ``core/lib/class.plx.plugins``) qui sert à définir les endroits du code de PluXml qui pourront être « hookés ».

La méthode callHook accepte 2 paramètres :

* le nom du hook appelé (obligatoire).
* un ou plusieurs paramètres passés à la fonction du hook appelé (option)

Le nom des hooks est normalisé de la façon suivante :

.. code:: none

    <nom du fichier/classe><nom de la méthode><nom de l’emplacement>

**Exemples :**

plxShowPagination

.. code:: none

    Fichier : core/lib/class.plx.show.php
    Class : plxShow
    Méthode : pagination()

plxMotorConstruct

.. code:: none

    Fichier : core/lib/class.plx.motor.php
    Class : plxMotor
    Méthode : __construct()

plxAdminEditUsersUpdate

.. code:: none

    Fichier : core/lib/class.plx.admin.php
    Class : plxAdmin
    Méthode : editUsers()
    Emplacement : Update, partie de mise à jour des utilisateurs

AdminTopEndHead

.. code:: none

    Fichier : core/admin/top.php
    Méthode : Header du fichier (balises </head>)

Liste des hooks
---------------

Cette liste peut être modifiée et complétée en fonction des évolutions de PluXml.

**/core/admin/article.php**

.. code:: none

    AdminArticleContent
    AdminArticleFoot
    AdminArticleInitData
    AdminArticleParseData
    AdminArticlePostData
    AdminArticlePrepend
    AdminArticlePreview
    AdminArticleSidebar
    AdminArticleTop

**/core/admin/auth.php**

.. code:: none

    AdminAuthPrepend
    AdminAuthEndHead
    AdminAuthTop
    AdminAuth
    AdminAuthEndBody
    AdminAuthBegin
    AdminAuthTopLostPassword
    AdminAuthLostPassword
    AdminAuthTopChangePassword
    AdminAuthChangePassword
    AdminAuthTopChangePasswordError
    AdminAuthChangePasswordError

**/core/admin/categorie.php**

.. code:: none

    AdminCategoryPrepend
    AdminCategoryTop
    AdminCategory
    AdminCategoryFoot

**/core/admin/categories.php**

.. code:: none

    AdminCategoriesPrepend
    AdminCategoriesTop
    AdminCategoriesFoot

**/core/admin/comment.php**

.. code:: none

    AdminCommentPrepend
    AdminCommentTop
    AdminComment
    AdminCommentFoot

**/core/admin/comments.php**

.. code:: none

    AdminCommentsPrepend
    AdminCommentsTop
    AdminCommentsPagination
    AdminCommentsFoot
    AdminCommentNewPrepend
    AdminCommentNewTop
    AdminCommentNew
    AdminCommentNewList
    AdminCommentNewFoot

**/core/admin/foot.php**

.. code:: none

    AdminFootEndBody

**/core/admin/index.php**

.. code:: none

    AdminIndexPrepend
    AdminIndexTop
    AdminIndexPagination
    AdminIndexFoot

**/core/admin/medias.php**

.. code:: none

    AdminMediasPrepend
    AdminMediasTop
    AdminMediasFoot
    AdminMediasUpload

**/core/admin/parametres_affichage.php**

.. code:: none

    AdminSettingsDisplayTop
    AdminSettingsDisplay
    AdminSettingsDisplayFoot

**/core/admin/parametres_avances.php**

.. code:: none

    AdminSettingsAdvancedTop
    AdminSettingsAdvanced
    AdminSettingsAdvancedFoot

**/core/admin/parametres_base.php**

.. code:: none

    AdminSettingsBaseTop
    AdminSettingsBase
    AdminSettingsBaseFoot

**/core/admin/parametres_edittpl.php**

.. code:: none

    AdminSettingsEdittplTop
    AdminSettingsEdittpl
    AdminSettingsEdittplFoot

**/core/admin/parametres_infos.php**

.. code:: none

    AdminSettingsInfos

**/core/admin/parametres_plugins.php**

.. code:: none

    AdminSettingsPluginsTop
    AdminSettingsPluginsFoot

**/core/admin/parametres_themes.php**

.. code:: none

    AdminThemesDisplay
    AdminThemesDisplayFoot
    AdminThemesDisplayTop

**/core/admin/parametres_users.php**

.. code:: none

    AdminSettingsUsersTop
    AdminSettingsUsersFoot

**/core/admin/prepend.php**

.. code:: none

    AdminPrepend

**/core/admin/profil.php**

.. code:: none

    AdminProfilPrepend
    AdminProfilTop
    AdminProfil
    AdminProfilFoot

**/core/admin/statique.php**

.. code:: none

    AdminStaticPrepend
    AdminStaticTop
    AdminStatic
    AdminStaticFoot

**/core/admin/statiques.php**

.. code:: none

    AdminStaticsPrepend
    AdminStaticsTop
    AdminStaticsFoot

**/core/admin/top.php**

.. code:: none

    AdminTopEndHead
    AdminTopMenus
    AdminTopBottom

**/core/admin/user.php**

.. code:: none

    AdminUserPrepend
    AdminUserTop
    AdminUser
    AdminUserFoot

**/core/lib/class.plx.admin.php**

.. code:: none

    plxAdminConstruct
    plxAdminEditConfiguration
    plxAdminHtaccess
    plxAdminEditProfil *
    plxAdminEditProfilXml
    plxAdminEditUsersUpdate
    plxAdminEditUsersXml
    plxAdminEditUser
    plxAdminEditCategoriesNew
    plxAdminEditCategoriesUpdate
    plxAdminEditCategoriesXml
    plxAdminEditCategorie
    plxAdminEditStatiquesUpdate
    plxAdminEditStatiquesXml
    plxAdminEditStatique
    plxAdminEditArticle *
    plxAdminEditArticleXml
    plxAdminDelArticle */core/lib/class.plxfeed.php
    plxFeedConstruct
    plxFeedPreChauffageBegin *
    plxFeedPreChauffageEnd
    plxFeedDemarrageBegin *
    plxFeedDemarrageEnd
    plxFeedRssArticlesXml
    plxFeedRssCommentsXml
    plxFeedAdminCommentsXml

**/core/lib/class.plx.motor.php**

.. code:: none

    plxMotorConstruct
    plxMotorPreChauffageBegin *
    plxMotorPreChauffageEnd
    plxMotorDemarrageBegin *
    plxMotorDemarrageEnd
    plxMotorDemarrageNewCommentaire
    plxMotorDemarrageCommentSessionMessage
    plxMotorGetCategories
    plxMotorGetStatiques
    plxMotorGetUsers
    plxMotorParseArticle
    plxMotorParseCommentaire
    plxMotorRedir301
    plxMotorNewCommentaire *
    plxMotorAddCommentaire *
    plxMotorAddCommentaireXml
    plxMotorSendDownload *

**/core/lib/class.plx.show.php**

.. code:: none

    plxShowConstruct
    plxShowPageTitle *
    plxShowMeta *
    plxShowLastCatList *
    plxShowArtTags *
    plxShowArtFeed *
    plxShowLastArtList *
    plxShowComFeed *
    plxShowLastComList *
    plxShowStaticListBegin *
    plxShowStaticListEnd *
    plxShowStaticContentBegin*
    plxShowStaticContent
    plxShowStaticInclude *
    plxShowPagination *
    plxShowTagList *
    plxShowArchList *plxShowPageBlog *
    plxShowTagFeed *
    plxShowTemplateCss *
    plxShowCapchaQ *
    plxShowCapchaR *

**/index.php**

.. code:: none

    Index
    IndexBegin
    IndexEnd

**/sitemap.php**

.. code:: none

    SitemapStatics
    SitemapCategories
    SitemapArticles
    SitemapBegin
    SitemapEnd

**/feed.php**

.. code:: none

    FeedBegin
    FeedEnd

**Hooks des thèmes**

.. code:: none

    ThemeEndHead
    ThemeEndBody

\* *Hooks acceptant une valeur de retour permettant d’interrompre l’exécution du code suivant l’appel du hook. Voir chapitre « Interrompre une fonction de PluXml ».*

Création d’un hook
------------------

Ajouter un hook
~~~~~~~~~~~~~~~

L’ajout d’un hook se fait par l’instruction

    $this->addHook

Exemple :

    $this->addHook('AdminTopEndHead', 'AdminTopEndHead');

* 1er paramètre : nom du hook tel qu’il est défini dans la liste des hooks disponibles.
* 2ième paramètre : nom de la méthode à exécuter lorsque le hook est appelé. Cette méthode fait partie de la classe du plugin.

Exemple :

    <?php
        class test extends plxPlugin {
            public function __construct($default_lang) {
                # Appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # Déclaration des hooks
                $this->addHook('AdminTopEndHead', 'AdminTopEndHead');
            }
            public function AdminTopHead() {
                echo '<script src="'.PLX_PLUGINS.'test/test.js"></script>';
            }
        }
    ?>

Dans cet exemple, le hook va ajouter dans le fichier *core/admin/top.php* le code suivant avant la balise \</head\>

    <script src="../../plugins/test/test.js"></script>

!!! note
    Il est conseillé de nommer la méthode avec même nom que le hook.
