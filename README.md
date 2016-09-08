# proxy4sparkui
Configure nginx on the master node for a reverse proxy to Apache Spark web UI and history server. No more ssh socks/tunnel.

# Dependencies
* nginx-1.9.4 or later
* Recompile nginx with http_sub_module and subs_filter_module enabled 

  ./configure [other options] --with-http_sub_module --add-module=/path/to/ngx_http_substitutions_filter_module

# Installation
* Change to the matching branch (spark version), e.g. 1.6.x or 2.0.x
* Copy `nginx/sparkui.conf` and `nginx/sparkhistory.conf` into `/etc/nginx/conf.d/`
* Edit the port in the config files
* Restart nginx

# Authentication
* Uncomment authentication directives in the config files
```
        #auth_basic           "private hosts";
        #auth_basic_user_file /etc/nginx/htpasswd;
```
* Create htpasswd
```
  htpasswd [-c] /etc/nginx/htpasswd user1
```
* Restart nginx

