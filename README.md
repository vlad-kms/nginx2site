## n2ensite, n2dissite
Сделано по аналогии с a2ensite, a2dissite
Подобно этим скриптам, подключают конфигурационные файлы сайтов в nginx (n2ensite) или отключают (n2dissite)
Использование:
    
    n2ensite <список файлов конфигурации сайтов>
    echo <список файлов конфигурации сайтов> | n2ensite
    echo <список 1 файлов конфигурации сайтов> | n2ensite <список 2 файлов конфигурации сайтов>

    n2dissite <список файлов конфигурации сайтов>
    echo <список файлов конфигурации сайтов> | n2dissite
    echo <список 1 файлов конфигурации сайтов> | n2dissite <список 2 файлов конфигурации сайтов>

В списках для указания файлов можно использовать шаблоны (*,?)

Примеры:

    n2ensite site1.conf site2 ~/nginx.cfg/site3
    echo "site1.conf site2" | n2ensite ~/nginx.cfg/site3
    echo "site1.conf" | n2ensite site2 ~/nginx.cfg/site3
    Эти команды создадут symlink'и для трех конфигураций сайтов
    /etc/nginx/sites-available/site1.conf  ln-> /etc/nginx/sites-enable/site1.conf
    /etc/nginx/sites-available/site2.conf  ln-> /etc/nginx/sites-enable/site2.conf
    ~/nginx.cfg/site3.conf                 ln-> /etc/nginx/sites-enable/site3.conf

    d2dissite site1 site3.conf
    echo "site1 site3.conf" | d2dissite
    echo "site1" | d2dissite site3.conf
    Эти команды удалят файлы двух конфигураций сайтов
    /etc/nginx/sites-enable/site1.conf
    /etc/nginx/sites-enable/site3.conf

    n2dissite *
    echo * | n2dissite
    Эта команда удалит все файлы *.conf из каталога /etc/nginx/sites-enable
    