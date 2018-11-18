# NGINX, configuration pour PluXml

## Où déposer la configuration

Ci-dessous, vous trouverez des exemples de fichiers de configuration pour le serveur web NGINX. Cet exemple rend possible l'utilisation de la réécriture d'url.

Le fichier doit être placé dans l'un de ces deux emplacements :
* /etc/nginx/conf.d/
* /etc/nginx/sites-enabled/

Vérifiez néanmoins que le fichier */etc/nginx/nginx.conf* contient bien les lignes *include /etc/nginx/conf.d/\*.conf;* ou *include /etc/nginx/sites-enabled/\*;*

[Voir la documentation Ngin](http://nginx.org/en/docs/http/ngx_http_core_module.html)

## Cas 1 : Tout en HTTP

    server {
        listen 80;
        server_name nom_du_site;

        root    /var/www/PluXml;
        index  index.php;

        # client_header_buffer_size 1k;
        # client_max_body_size 1m;
        client_max_body_size 8m; # évite une erreur 413 si on upload un fichier

        ## BASE

        # Règle principale
        location / {
            try_files $uri $uri/ @handler;
        }

        # Réécriture vers l'index
        location @handler {
            rewrite ^/(.*)$ /index.php?^$1 last;
        }

        # Parseur PHP
        location ~ \.php$ {
            fastcgi_split_path_info ^(.+\.php)(/.+)$;
            # NOTE: Utilisez "cgi.fix_pathinfo = 0;" dans php.ini
            include fastcgi.conf;
            fastcgi_index index.php;

            # Utilisez PHP5 ou PHP7, mais pas les deux
            # fastcgi_pass unix:/run/php5-fpm.sock;
            fastcgi_pass unix:/run/php/php7.0-fpm.sock;
            # Sous Alpinelinux v3.8, utiliser le socket comme suit :
            # fastcgi_pass unix:/run/php-fpm7/php-fpm.sock;
        }

        ## REDIRECTIONS

        # Flux RSS
        location /feed/ {
            rewrite ^/feed\/(.*)$ /feed.php?^$1 last;
        }

        # Sitemap
        location = /sitemap.xml {
            rewrite .* /sitemap.php;
        }

        ## PROTECTION REPERTOIRES

        location ~ /(version|update|readme|data/configuration) {
            deny all;
        }

        ## CACHING
        # https://www.theodo.fr/blog/2016/06/improve-the-performance-of-your-webapp-configure-nginx-to-cache/
        # http://www.supinfo.com/articles/single/2843-implementer-cache-navigateur-avec-nginx

        # cache-control
        location /data/ {
    	add_header Cache-Control public;
    	expires 12h;
        }
        location /core/ {
    	add_header Cache-Control public;
    	expires 12h;
        }
        location /plugins/ {
    	add_header Cache-Control public;
    	expires 12h;
        }
        location /themes/ {
    	add_header Cache-Control public;
    	expires 12h;
        }

    }

## Cas 2 : Site HTTP et administration HTTPS

C'est un cas hybride que vous pouvez utiliser si vous n'avez pas de bonnes performances en HTTPS mais que vous voulez tout de même sécuriser l'administration.

    # Paramètrage du socket PHP
    upstream PHP_SOCKET {
        # Utilisez PHP5 ou PHP7, mais pas les deux
        #server unix unix:/run/php5-fpm.sock;
        server unix:/run/php/php7.0-fpm.sock;
        # Sous Alpinelinux v3.8, utiliser le socket comme suit :
        # fastcgi_pass unix:/run/php-fpm7/php-fpm.sock;
    }

    server {
        listen 80;
        server_name nom_du_site;

        root    /var/www/PluXml;
        index  index.php;

        ## BASE

        # Règle principale
        location / {
            try_files $uri $uri/ @handler;
        }

        # Réécriture vers l'index
        location @handler {
            rewrite ^/(.*)$ /index.php?^$1 last;
        }

        # Parseur PHP
        location ~ \.php$ {
            fastcgi_split_path_info ^(.+\.php)(/.+)$;
            # NOTE: Utilisez "cgi.fix_pathinfo = 0;" dans php.ini
            include fastcgi.conf;
            fastcgi_index index.php;
            fastcgi_pass PHP_SOCKET; # This variable is set on top
        }

        ## REDIRECTIONS

        # L'admin est en HTTPS
        location /core/admin {
            return 301 https://$host$request_uri;
        }

        # Flux RSS
        location /feed/ {
            rewrite ^/feed\/(.*)$ /feed.php?^$1 last;
        }

        # Sitemap
        location = /sitemap.xml {
            rewrite .* /sitemap.php;
        }

        ## PROTECTION REPERTOIRES

        location ~ /(version|update|readme|data/configuration) {
            deny all;
        }

        ## CACHING
        # https://www.theodo.fr/blog/2016/06/improve-the-performance-of-your-webapp-configure-nginx-to-cache/
        # http://www.supinfo.com/articles/single/2843-implementer-cache-navigateur-avec-nginx

        # cache-control
        location /data/ {
    	add_header Cache-Control public;
    	expires 12h;
        }
        location /core/ {
    	add_header Cache-Control public;
    	expires 12h;
        }
        location /plugins/ {
    	add_header Cache-Control public;
    	expires 12h;
        }
        location /themes/ {
    	add_header Cache-Control public;
    	expires 12h;
        }
    }

    server {
        listen 443 ssl http2;
        server_name nom_du_site;

        ssl_certificate /path/to/certificate;
        ssl_certificate_key /path/to/key;

        root   /var/www/PluXml;
        index  index.php;

        # client_header_buffer_size 1k;
        # client_max_body_size 1m;
        client_max_body_size 8m; # évite une erreur 413 si on upload un fichier

        # Conserver ces URL en HTTPS
        location /core/    { try_files $uri $uri/ @handler; }
        location /plugins/ { try_files $uri @handler; }
        location /data/    { try_files $uri @handler; }
        location /themes/  { try_files $uri @handler; }
        location /preview  { try_files $uri @handler; }

        # Redirection des autres URL vers HTTP
        location / {
            return 302 http://$host$request_uri;
        }

        # Réécriture vers l'index
        location @handler {
            rewrite ^/(.*)$ /index.php?^$1 last;
        }

        # Parseur PHP
        location ~ \.php$ {
            fastcgi_split_path_info ^(.+\.php)(/.+)$;
            include       fastcgi.conf;
            fastcgi_index index.php;
            fastcgi_pass  php_socket;
        }
    }

## Cas 3 : Tout en HTTPS

    server {
        listen 443 ssl http2;
        server_name nom_du_site;

        ssl_certificate /path/to/certificate;
        ssl_certificate_key /path/to/key;

        root    /var/www/PluXml;
        index  index.php index.html;

        # client_header_buffer_size 1k;
        # client_max_body_size 1m;
        client_max_body_size 8m; # évite une erreur 413 si on upload un fichier

        ## BASE

        # Règle principale
        location / {
            try_files $uri $uri/ @handler;
        }

        # Réécriture vers l'index
        location @handler {
            rewrite ^/(.*)$ /index.php?^$1 last;
        }

        # Parseur PHP
        location ~ \.php$ {
            fastcgi_split_path_info ^(.+\.php)(/.+)$;
            # NOTE: Utilisez "cgi.fix_pathinfo = 0;" dans php.ini
            include fastcgi.conf;
            fastcgi_index index.php;

            # Utilisez PHP5 ou PHP7, mais pas les deux
            # fastcgi_pass unix:/run/php5-fpm.sock;
            fastcgi_pass unix:/run/php/php7.0-fpm.sock;
            # Sous Alpinelinux v3.8, utiliser le socket comme suit :
            # fastcgi_pass unix:/run/php-fpm7/php-fpm.sock;
        }

        ## REDIRECTIONS

        # Flux RSS
        location /feed/ {
            rewrite ^/feed\/(.*)$ /feed.php?^$1 last;
        }

        # Sitemap
        location = /sitemap.xml {
            rewrite .* /sitemap.php;
        }

        ## PROTECTION REPERTOIRES

        location ~ /(version|update|readme|data/configuration) {
            deny all;
        }

        ## CACHING
        # https://www.theodo.fr/blog/2016/06/improve-the-performance-of-your-webapp-configure-nginx-to-cache/
        # http://www.supinfo.com/articles/single/2843-implementer-cache-navigateur-avec-nginx

        # cache-control
        location /data/ {
    	add_header Cache-Control public;
    	expires 12h;
        }
        location /core/ {
    	add_header Cache-Control public;
    	expires 12h;
        }
        location /plugins/ {
    	add_header Cache-Control public;
    	expires 12h;
        }
        location /themes/ {
    	add_header Cache-Control public;
    	expires 12h;
        }
    }

    server {
        listen 80;
        server_name nom_du_site;

        # Tout doit être en HTTPS
    	return 301 https://$host$request_uri;
    }

## Notes sur les fichiers de configuration

__Gestion du HTTP/2__

Les configurations proposée ci-dessous pour HTTPS utilisent HTTP/2 (cas 2 et cas 3). Cette nouvelle version du protocole HTTP est disponible à partir de NGINX 1.9.5. Si vous utilisez une version plus ancienne, supprimez *http2* dans la ligne *listen 443 ssl http2;* sinon NGINX ne pourra pas démarrer.

__Attention__, pour fonctionner il faut remplacer les valeurs des variables sur les lignes suivantes :

* *server_name nom_du_site;* : "nom_du_site" doit être remplacé par le DNS ou l'adresse IP de votre serveur, vous pouvez également le remplacer par *localhost* si vous lancez le serveur web en local sur votre machine. Exemple : *server_name pluxml.org www.pluxml.org 5.123.123.321;*
* *root /var/www/PluXml;*  : modifier le chemin d'accès root */var/www/PluXml* si l'archive Zip de PluXml a été décompréssée dans un répertoire différent.
* Si vous utilisez php5, décommentez la ligne *fastcgi_pass unix:/run/php5-fpm.sock;* (en supprimant le "#" devant la ligne) et commentez la ligne *fastcgi_pass unix:/run/php/php7.0-fpm.sock;* (en ajoutant un "#" devant la ligne). Inversement si vous utilisez php7.
