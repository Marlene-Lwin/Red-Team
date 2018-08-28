# Trusted Domain Redirect with Powershell Empire

```
# To Set Up Powershell Empire Team Server
Enter “listeners”
Enter “uselistener http”
set Name httpScriptkiddie
set Host http://scriptkiddie.ninja:80
set Port 5000
execute

vim /var/www/html/.htaccess
RewriteEngine On
RewriteCond %{REQUEST_URI} ^/(admin/get.php|login/process.php|news.php)/?$ [NC]
RewriteRule ^.*$ http://<PRIVATE IP addr of Empire>:<Empire listener port - 5000>%{REQUEST_URI} [P]
RewriteRule ^.*$ https://google.com/ [L,R=302]

Final Step Go back to Empire teamserver
usestager multi/launcher httpScriptkiddie

#Domain Naming

Hackinglab.beer – teamserer
Log into Namecheap.com
Select “Domain list” on the left
Select “Manage” by the domain you wish to configure
One of my domains is Hackinglab.beer for the teamserver
Select “Advance DNS” tab at the top
Select “Add new record”
Select “A record” for type
Enter “empire” for host
Enter “<EC2 public IP addr for Empire teamserver>” for value
Select the check mark to save record


Scriptkiddie.ninja – c2
Select “Domain list” on the left
Select “Manage” by the domain you wish to configure
One of my domains is scriptkiddie.ninja for my C2
Select “Advance DNS” tab at the top
Select “Add new record”
Select “A record” for type
Enter “@” for host
Enter “<EC2 public IP addr for C2>” for value
Select the check mark to save record
```
