# Apache

  Forbidden - _You don't have permission to Access / on this server_

{% code-tabs %}
{% code-tabs-item title="C:\\wamp64\\bin\\apache\\apache2.4.18\\conf\\extra\\httpd-vhosts.conf" %}
```text
#
# Virtual Hosts
#

<VirtualHost *:8080>
	ServerName localhost
	DocumentRoot c:/wamp64/www
	<Directory  "c:/wamp64/www/">
		Options +Indexes +FollowSymLinks +MultiViews
		AllowOverride All
		#Require local
		Require all granted
	</Directory>
</VirtualHost>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="C:\\wamp64\\bin\\apache\\apache2.4.18\\conf\\httpd.conf" %}
```text
DocumentRoot "c:/wamp64/www"
<Directory "c:/wamp64/www/">
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
    #   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # http://httpd.apache.org/docs/2.4/mod/core.html#options
    # for more information.
    #
    #Options +Indexes +FollowSymLinks
	Options Indexes FollowSymLinks

    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   AllowOverride FileInfo AuthConfig Limit
    #
    AllowOverride All

    #
    # Controls who can get stuff from this server.
    #

#   onlineoffline tag - don't remove
    #Require local
	Require all granted
	#Order Deny,Allow
	#Allow from 20.10.1.160
	#Allow from 127.0.0.1
</Directory>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

