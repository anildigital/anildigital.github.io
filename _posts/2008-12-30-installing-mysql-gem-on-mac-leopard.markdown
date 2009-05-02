---
wordpress_id: 343
layout: post
title: Installing MySQL gem on Mac Leopard
wordpress_url: http://anilwadghule.com/blog?p=343
---

If you are getting following error on trying to install mysql gem on mac (Leopard, in my case)

<pre class="terminal">
$ sudo gem install mysql
Building native extensions.  This could take a while...
ERROR:  Error installing mysql:
ERROR: Failed to build gem native extension.

/System/Library/Frameworks/Ruby.framework/Versions/1.8/usr/bin/ruby extconf.rb install mysql checking for mysql_query() in -lmysqlclient... no checking for main() in -lm... yes checking for mysql_query() in -lmysqlclient... no checking for main() in -lz... yes checking for mysql_query() in -lmysqlclient... no checking for main() in -lsocket... no checking for mysql_query() in -lmysqlclient... no checking for main() in -lnsl... no checking for mysql_query() in -lmysqlclient... no extconf.rb failed Could not create Makefile due to some reason, probably lack of necessary libraries and/or headers.  Check the mkmf.log file for more details.  You may need configuration options.
</pre>

Try following

<pre class="terminal">
$ sudo gem install mysql -- --with-mysql-config=/usr/local/mysql/bin/mysql_config
Building native extensions.  This could take a while...
Successfully installed mysql-2.7
1 gem installed

The above thing is correct only if you have installed 32 bit MySQL dmg. If you have installed 64 bit MySQL dmg, you are sure to get following error on running rails server or any ruby app using mysql gem

dyld: lazy symbol binding failed: Symbol not found: _mysql_init
  Referenced from: /Library/Ruby/Gems/1.8/gems/mysql-2.7/lib/mysql.bundle
  Expected in: dynamic lookup

dyld: Symbol not found: _mysql_init Referenced from: /Library/Ruby/Gems/1.8/gems/mysql-2.7/lib/mysql.bundle Expected in: dynamic lookup

Trace/BPT trap
</pre>

The reason is that MySQL Ruby gem build is 32 bit one and it doesn't work well with 64 bit MySQL dmg

To solve all this, uninstall installed 64 bit MySQL dmg as follows ( There is no good way to uninstall MySQL from Mac other than below)

<pre class="terminal">
 sudo rm /usr/local/mysql
 sudo rm -rf /usr/local/mysql*
 sudo rm -rf /Library/StartupItems/MySQLCOM
 sudo rm -rf /Library/PreferencePanes/My*
 edit /etc/hostconfig and remove the line MYSQLCOM=-YES-
 sudo rm -rf /Library/Receipts/mysql*
 sudo rm -rf /Library/Receipts/MySQL*
</pre>
from - [http://akrabat.com/2008/09/11/uninstalling-mysql-on-mac-os-x-leopard/](http://akrabat.com/2008/09/11/uninstalling-mysql-on-mac-os-x-leopard/)

Now download and install 32 bit [MySQL dmg](http://dev.mysql.com/downloads/mysql/5.1.html#macosx-dmg)
