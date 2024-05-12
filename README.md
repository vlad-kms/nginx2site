## n2ensite, n2dissite
Сделано по аналогии с a2ensite, a2dissite
Подобно этим скриптам, подключают конфигурационные файлы сайтов в nginx (n2ensite) или отключают (n2dissite)

Использование:

    n2ensite site1.conf site2 ~/nginx.cfg/site3
    Эта команда создаст symlink'и для трех конфигураций сайтов
    /etc/nginx/sites-available/site1.conf  ln-> /etc/nginx/sites-enable/site1.conf
    /etc/nginx/sites-available/site2.conf  ln-> /etc/nginx/sites-enable/site2.conf
    ~/nginx.cfg/site3.conf                 ln-> /etc/nginx/sites-enable/site3.conf

    d2dissite site1 site3.conf
    Эта команда удалит symlink'и для двух конфигураций сайтов
    /etc/nginx/sites-enable/site1.conf
    /etc/nginx/sites-enable/site3.conf

    for file in /etc/nginx/sites-enabled/*.conf; do ./n2dissite $file; done
    Эта команда удалит все symlink *.conf из каталога /etc/nginx/sites-enable
    