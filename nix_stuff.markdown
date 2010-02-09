pwgen a really random password with length 8-15 characters
    pwgen $[($RANDOM % ($[15-8]+1)) + 8] -cnsB1

System Info
    uname -a

Processes
    ps -ax

Free Memory
    free -m

Version:
    cat /etc/lsb-release

fix nano to backspace delete rather than 'delete'
    sudo nano /etc/nanorc
    set rebinddelete

## Apache
Restart Apache on Ubuntu:
    /etc/init.d/apache2 restart

Location of sites-available on Ubuntu:
    /etc/apache2/sites-available/

Enable a site:
    a2ensite site_name

Disable a site:
    a2dissite site_name
