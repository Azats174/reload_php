# reload_php
check php pool include curl and nginx.
create  php-stat  site
_______________________________________
location /status/www {
                include         fastcgi_params;
                fastcgi_pass    unix:/run/php5-fpm.sock;
                fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        }
_________________________________________
www is name pool

curl --head -sf http://localhost/status/www/all  ||     pkill -f "php-fpm: pool www"

If an error is returned on the request, the problem pool is restarted
