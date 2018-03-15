[![Build Status](https://travis-ci.org/Revasz/yiimp.svg?branch=AllBranchesMerged)](https://travis-ci.org/Revasz/yiimp)

***yiimp*** - crypto-mining-pool-framework.<br/>
Forked from [*yaamp*](https://github.com/globalzon/yaamp) and based on the [*yii-framework*](http://www.yiiframework.com/).

Originally developed by [*globalzon*](https://github.com/globalzon/yaamp), now maintained and further enhanced by [*tpruvot*](https://github.com/tpruvot/yiimp/tree/next)<br/>and various users from [*GitHub*](https://github.com/).
_____

**Required:**

	Linux, MySQL/MariaDB, php7.0+, Memcached, a web-server (Lighttpd or Nginx recommended).
_____

**Basic configuration for *Nginx*:**

	location / {
		try_files $uri @rewrite;
	}

	location @rewrite {
		rewrite ^/(.*)$ /index.php?r=$1;
	}

	location ~ \.php$ {
		fastcgi_pass unix:/var/run/php7.0-fpm.sock;
		fastcgi_index index.php;
		include fastcgi_params;
	}
_____

**If you use *Apache*, it should look something like this. (Already set in web/.htaccess):**

	RewriteEngine on

	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteRule ^(.*) index.php?r=$1 [QSA]
_____

**If you use *Lighttpd*, use the following, basic, configuration:**

	$HTTP["host"] =~ "YourServerName" {
	        server.document-root = "/var/web"
	        url.rewrite-if-not-file = (
			"^(.*)/([0-9]+)$" => "index.php?r=$1&id=$2",
			"^(.*)\?(.*)" => "index.php?r=$1&$2",
	                "^(.*)" => "index.php?r=$1",
	                "." => "index.php"
	        )

		url.access-deny = ( "~", ".dat", ".log" )
	}
_____

For the database, import the initial dump present in the *yiimp/sql* folder.

Then, apply the migration scripts to be in sync with the current git, they are sorted by date of change.

The recommended install folder for the stratum engine is */var/stratum .*<br/>
Copy all the *.conf* files, *run.sh*, the *stratum* binary<br/>
and the *blocknotify* binary to this folder.

Your database need at least 2 users, one for the web site (*php7.0+*)<br/>
and one for the *stratum* connections.<br/>
(password set in */var/stratum/config/algo.conf*)

Some scripts are expecting the web folder to be */var/web*.<br/>
You can use directory *symlinks*.
_____

**Add your exchange *API* public and secret keys in these two separated files:**

	/etc/yiimp/keys.php       - Fixed path in code.
	/var/web/serverconfig.php - Use sample as basic configuration.

You can find sample configuration files in<br/>
*/var/web/serverconfig.sample.php*<br/>
and<br/>
*/var/web/keys.sample.php*.

This web application includes some command line tools, add the */bin* folder from */yiimp* to your *PATH*<br/>
and type *yiimp* to list them, *yiimp checkup* can help to test your initial setup.<br/>
Future scripts and maybe the *cron* jobs will then use this *yiic* interface.
_____

**You need at least three backend shells (in *screen*) running these scripts:**

	/var/web/main.sh
	/var/web/loop2.sh
	/var/web/block.sh
_____

**Start one *stratum* per algorithm using the *run.sh2* script with the algorithm as parameter.<br/>
For example, for *x11*:**

	run.sh x11

Edit each *.conf* file with proper values.

Look at *rc.local*, it starts all three backend shells and all *stratum* processes.<br/>
Copy it to the */etc* folder so that all *screen-shells* are started on (re)boot.
_____

**All your *coin's* configuration files need to *blocknotify*<br/>
their corresponding *stratum* using something like this:**

	blocknotify=blocknotify yourserver.any:port coinid %s

On your, new *yiimp*, website, go to *yourserver.any/site/adminRights* to login as administrator.<br/>
You have to change it to something different in the code (*/var/web/yaamp/modules/site/SiteController.php*).<br/>
A real *administrator* login may be added later, but you can setup a password authentication with your web server.
_____

**Sample for *Lighttpd*:**

	htpasswd -c /etc/yiimp/admin.htpasswd <adminuser>
_____

**And in the *Lighttpd* configuration file:**

	# Admin access
	$HTTP["url"] =~ "^/site/adminRights" {
	        auth.backend = "htpasswd"
	        auth.backend.htpasswd.userfile = "/etc/yiimp/admin.htpasswd"
	        auth.require = (
	                "/" => (
	                        "method"  => "basic",
	                        "realm"   => "Yiimp Administration",
	                        "require" => "valid-user"
	                )
	        )
	}
_____

Finally, remove the *IP-filter-check* in */var/web/yaamp/modules/site/SiteController.php*.<br/>

There are logs generated in the */var/stratum* folder and */var/log/stratum/debug.log* for the *php7.0+* log.
_____

**CREDITS:**

Thanks to [*globalzon*](https://github.com/globalzon) for the release of the [*yaamp-sourcecode*](https://github.com/globalzon/yaamp).<br/>

Thanks to [*tpruvot*](https://github.com/tpruvot) for further developing and maintaining the [*yiimp-repository*](https://github.com/tpruvot/yiimp).<br/>

This *fork* contains patches, that seemed useful to me, from the following users/repositories:<br/>
(In no particular order.)
	
https://github.com/crackfoo/yiimp
		
https://github.com/Tristian/yiimp
		
https://github.com/AlmazDelDiablo/yiimp
		
https://github.com/Infernoman/yiimp
		
https://github.com/AltMinerNet/yiimp
		
https://github.com/Jaerin/yiimp
		
https://github.com/fastman/yiimp
		
https://github.com/phm87/yiimp
		
So, thanks to them too.

You can support this project by donating to [*tpruvot*](https://github.com/tpruvot):

	BTC: 1Auhps1mHZQpoX4mCcVL8odU81VakZQ6dR
	
and/or [*Revasz*](https://github.com/Revasz) (The maintainer of this  fork.)

	BTC: 1i6yhynkkaDN2Y1RiNoZRxcQkEELdePUV
 
	ETH: 0x222eD19EAA80eE530B55b3a8394cF841DFb41Af6

	XMR: 4AbuFAvg6wUKxH4uZafgcyJuUkksxiZBz1N8sNvtQbYNe9bDfCnSFxcPs3ZPfaeDzNc9rWorxw4piBvEpuKvWL8dPSJxcPu

	BCH: 1Po5XaiwZg8iWDjZDwoNU7M56DpxRmkmed
_____

***Revasz,* 2018**
