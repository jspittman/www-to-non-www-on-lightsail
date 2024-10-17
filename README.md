# www to non www on an Amazon Lightsail Wordpress Instance

Steps to Resolve www to non-www redirection on an Amazon Lightsail Wordpress Instance

Interestingly, Bitnomi uses the wordpress-vhost.conf and wordpress-https-vhost.conf files to derive their httpd.conf instructions.

This page does a good job of explanin the solution: https://stackoverflow.com/questions/75256820/redirection-www-to-non-www-in-aws-lightsail

You'll want to navigate to: /opt/bitnami/apache/conf/vhosts

Then edit: wordpress-vhost.conf and wordpress-https-vhost.conf.  Edit as you would when modifying httpd.conf.  Then save, close, and restart your server.

You can use sudo nano wordpress-https-vhost.conf, and sudo nano wordpress-vhost.conf to edit in terminal.

This code worked for me:

    RewriteEngine On
    RewriteCond %{HTTP_HOST} ^www\.(.*)$ [NC]
    RewriteRule ^(.*)$ https://%1/$1 [R=301,L]

Best of luck and happy coding! - Jeff
