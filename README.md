perl-scripts
============

mka2host
--------
Allows the creation of Virtual Hosts in apache with one simple command, <code>mka2host &lt;host&gt;</code>

you can also pass it things like a user to own the directory and admin information. 

The PHP control on this uses mod\_actions and mod\_fastcgi by default. this is the
way its configured to use this method if you wish.

<pre>
&lt;IfModule mod_fastcgi.c&gt;
  AddHandler fastcgi-script .fcgi
  #FastCgiWrapper /usr/lib/apache2/suexec
  FastCgiIpcDir /var/lib/apache2/fastcgi
&lt;/IfModule&gt;
&lt;IfModule mod_fastcgi.c&gt;
  AddHandler php5-fcgi .php
  Action php5-fcgi /cgi-bin/php5.external
  &lt;Location "/cgi-bin/php5.external"&gt;
    Order Deny,Allow
    Deny from All
    Allow from env=REDIRECT_STATUS
  &lt;/Location&gt;
&lt;/IfModule&gt;
</pre>


mknxhost
--------
    The same as above only written for nginx, the admin information isn't included on this one nor 
is CGI stuff due to how nginx is designed, there is however support for nginx's HttpFastcgiModule for
PHP.
