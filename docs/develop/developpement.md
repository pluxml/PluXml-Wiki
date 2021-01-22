## Utiliser les hooks prédéfinis pour les thèmes
Il existe deux hooks prédéfinis pour être utilisé dans les thèmes : *ThemeEndHead* et *ThemeEndBodyHook*

### ThemeEndHead
Le hook *ThemeEndHead* permet d’injecter du code dans la balise *head* dans la page du site coté visiteurs. Voilà un exemple qui ajoute dans la balise head l’appel du fichier javascript *fichier.js* :

    <?php
        class test extends plxPlugin {
            public function __construct($default_lang) {
                # appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # déclaration du hook
                $this->addHook('ThemeEndHead', 'ThemeEndHead');
            }
            public function ThemeEndHead() {?>
                <script type="text/javascript" src="fichier.js"></script>
                <?php
            }
        }
    ?>


### Hook ThemeEndBody
Le hook *ThemeEndBody* permet d’injecter du code dans la balise body dans la page du site coté visiteurs. Voilà un exemple qui ajoute dans la balise du code javascript :

    <?php
        class test extends plxPlugin {
            public function __construct($default_lang) {
                # appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # déclaration du hook
                $this->addHook('ThemeEndHead', 'ThemeEndHead');
            }
            public function ThemeEndHead() {?>
                <script type="text/javascript">
                    <!—-
                    function myfunction(text) {
                    alert(text);
                    }
                    -->
                </script>
                <?php
            }
        }
    ?>

## Créer ses propres hooks
### Hooks utilisateur
Il est possible de définir ses propres noms de hooks et de les appeler dans les thèmes. Nous connaissons déjà la liste des hooks réservés au fonctionnement de PluXml, mais il est tout à fait possible de définir ses propres hooks.

Voyons le cas suivant : nous souhaitons définir un hook qui agira dans le fichier *sidebar.php* du dossier theme. Nous appellerons ce hook *SidebarTest* afin de respecter la nomenclature des noms des hooks.

Commençons par écrire notre plugin :

    <?php
        class test extends plxPlugin {
            public $var='Hook de la sidebar';
            public function __construct($default_lang) {
                # appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # déclaration du hook
                $this->addHook('SidebarTest', 'SidebarTest');
            }
            public function SidebarTest() {
                echo $this->var;
            }
        }
    ?>

Nous retrouvons ici tous les composants décris dans les paragraphes précédents. Il s’agit ici d’afficher uniquement le message "Hook
de la sidebar", message définit dans la variable $var.

Modifions maintenant le fichier *sidebar.php* du thème afin de placer l’appel de notre hook.

    <?php if(!defined('PLX_ROOT')) exit; ?>
    <div id="sidebar">
        ...
    <?php eval($plxShow->callHook('SidebarTest')) ?>
    </div>


Nous utilisons ici la fonction *callHook* de *$plxShow* en passant en paramètre le nom du hook à traiter.

### Passage de paramètres à un hook
Un hook peut être appelé en lui passant un ou plusieurs paramètres.

Exemple :

    <?php eval($plxShow->callHook('MyHook', 'param1')) ?>

Pour appeler un hook avec plusieurs paramètres, il faut les passer sous forme de tableau.

    <?php eval($plxShow->callHook('MyHook', array('param1', 'param2'))) ?>

### Déclaration du hook recevant les paramètres
Soit le hook 'MyHook' appelé avec 2 paramètres valant chacun 'azerty' et 'qwerty' :

    <?php eval($plxShow->callHook('MyHook', array('azerty', 'qwerty'))) ?>
    <?php
        class test extends MyPlugin {
            public function __construct($default_lang) {
                # Appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # Déclaration des hooks
                $this->addHook('MyHook', 'MyHookFunction');
            }
            public function MyHookFunction($params) {
                echo $param[0];
                echo $param[1];
            }
        }
    ?>

Lorsque le hook *MyHook* est appelé, la fonction MyHookFunction est exécutée. Le paramètre *$params* de la fonction *MyHookFunction* reçoit les deux paramètres sous forme de tableau. Ainsi *$params[0]* contient la valeur 'azerty' et *$param[1]* la valeur 'qwerty'

Le hook MyHook affiche :

    azerty
    qwerty

### Valeur de retour d'un hook
Un hook peut retourner une valeur à la page appelante.

Exemple :

    <?php
        $retour = $plxShow->callHook('MyHook');
        echo $retour;
    ?>

!!! danger "Important"
    L'appel d'un hook renvoyant une valeur ne doit pas être fait avec la fonction eval.

La syntaxe suivante ne doit pas être utilisée :

    <?php $retour = eval($plxShow->callHook('MyHook')) ?>

Il est possible de combiner valeur de retour et passage de paramètres.

    <?php $retour = $plxShow->callHook('MyHook', 'azerty') ?>

Exemple :

    <?php
        class test extends MyPlugin {
            public function __construct($default_lang) {
                # Appel du constructeur de la classe plxPlugin (obligatoire)
                parent::__construct($default_lang);
                # Déclaration des hooks
                $this->addHook('MyHook', 'MyHookFunction');
            }
            public function MyHookFunction() {
                return 'Brian is in the kitchen :)';
            }
    ?>

La phrase 'Brian is in the kitchen :)' est renvoyée à la page appelante. L'instruction *echo $retour;* affichera cette phrase.

## Appeler un hook à partir d’une page statique

Il est tout a fait possible d’appeler un hook à partir d’une page statique.

Exemple :

    <?php
        global $plxShow;
        eval($plxShow->callHook('Static1Test'));
    ?>

Il faut dans un premier temps déclarer *$plxShow* en tant que variable globale.

    global $plxShow;

Pour appeler un hook, nous utilisons la fonction *callHook* de *$plxShow* en passant en paramètre le nom du hook à traiter. Le passage de paramètres et valeur de retour sont autorisés.

## Liste des constantes

PluXml dispose de constante contenant des valeurs prédéfinies et ne pouvant pas être modifiées :

* PLX_ADMIN : Contient la valeur true si on est dans l’administration de PluXml
* PLX_AUTHPAGE : Contient la valeur true si on est sur la page d’identification core/admin/auth.php
* PLX_CHARSET : Contient le charset utilisé par PluXml (utf-8 par défaut)
* PLX_CONF : Contient le chemin par defaut du fichier parametres.xml (PLX_ROOT.'data/configuration/parametres.xml')
* PLX_CONFIG_PATH : Contient le chemin par défaut vers le dossier data/configuration/
* PLX_CORE : Contient l’emplacement du dossier core (PLX_ROOT.'core/')
* PLX_DEBUG : Contient la valeur true en phase de développement pour charger ou non les fichiers javascript minimisés de PluXml et afficher les messages d’erreurs détaillés
* PLX_FEED : Contient la valeur true si on est sur le script feed.php
* PLX_MICROTIME : Contient les données du timer d’exécution des scripts renvoyées par getMicrotime()
* PLX_PLUGINS : Contient l’emplacement du dossier plugins (plugins/)
* PLX_ROOT : Contient le chemin relatif vers la racine du site par rapport au fichier courant (par exemple ./ ou ./../)
* PLX_UPDATE : Contient l’emplacement du dossier de mise à jour (PLX_ROOT.'update/')
* PLX_UPDATER : Contient la valeur true si on est sur le script de mise à jour de PluXml
* PLX_VERSION : Contient le n° de version de PluXml

## Comprendre le nom des fichiers xml des articles
PluXml n’utilise pas de base de données. Le contenu des articles est stocké dans des fichiers xml. Si vous utilisez la configuration par défaut, ces fichiers sont enregistrés dans le dossier *data/articles/*. Chaque nom de fichier est composé de certaines informations propre à l’article.

Exemple :

  _0001.002.001.201304251142.premier-article.xml

Si nous détaillons le nom du fichier, nous avons:

* _ est un caractère optionnel. Il indique que l'article est en attente de validation.
* 0001 est l'identifiant de l'article. Il peut aller jusqu'à 9999, donc 9999 articles.
* 002 contient l'identifiant de la catégorie dans laquelle l'article est classé. Il peut avoir plusieurs identifiants séparés par des virgules (exemple 001,002). Ici l'article est donc classé dans la catégorie 002. Il n'y a pas de limite dans le nombre de catégories possibles, du moment qu'elles sont bien séparées par des virgules. Il est possible d'avoir également la valeur draft qui indique que l'article est un brouillon, ou la valeur home qui indique que l'article est publié dans la catégorie *Page d'accueil*. Il est donc tout a fait possible d'avoir 0001.001,002,draft.001.201304251142.premier-article.xml
* 001 est l'identifiant de l'utilisateur qui a rédigé l'article.
* 201304251142 est la date de publication de l'article. Cela peut être une date future. Cette date est de la forme AAAAMMJJHHMM où:
    - AAAA = année
    - MM = mois
    - JJ = jour
    - HH = heure
    - MM = minute
* premier-article est l'url de l'article. On la retrouve dans : http://mondomaine.com/index.php?article1/premier-article
* xml est l'extension du fichier
