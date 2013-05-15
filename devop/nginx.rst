.. Nginx

Nginx
##################################################

Configuration
==================================================

`DirectiveIndex <http://wiki.nginx.org/DirectiveIndex>`_
`Configuration Example <http://wiki.nginx.org/FullExample>`_

Scripts
==================================================

* 切割日志
* 控制脚本


实践
==================================================
Nginx用redis作为缓存
--------------------------------------------------

1. 编译安装Nginx

::

   wget http://nginx.org/download/nginx-1.2.6.tar.gz
   tar -xzf nginx-1.26.tar.gz
   wget http://people.freebsd.org/~osa/ngx_http_redis-0.3.6.tar.gz
   tar -xzf ngx_http_redis-0.3.6.tar.gz
   wget https://nodeload.github.com/agentzh/echo-nginx-module/zip/v0.42
   wget https://nodeload.github.com/agentzh/echo-nginx-module/zip/v0.42
   wget https://nodeload.github.com/agentzh/redis2-nginx-module/zip/v0.09
   wget https://nodeload.github.com/agentzh/srcache-nginx-module/zip/v0.19
   wget https://nodeload.github.com/agentzh/set-misc-nginx-module/zip/v0.22rc8
   unzip *.zip
   cd nginx-1.2.6
   ./configure --prefix=/data/apps/nginx --add-module=../ngx_http_redis-0.3.6 --add-module=../echo-nginx-module-0.42 --add-module=../ngx_devel_kit-0.2.18 --add-module=../set-misc-nginx-module-0.22rc8 --add-module=../srcache-nginx-module-0.19 --add-module=../redis2-nginx-module-0.09 --with-pcre
   make && make install

2. 相关的配置
::

   
    location /redis_get {
        internal;
        set $redis_key $args;
        redis_pass backen_qisu_redis;
    }

    location /redis_set {
        internal;
        set $key $arg_key;
        redis2_query set $key $echo_request_body;
        redis2_query expire $key 120;
        redis2_pass backen_qisu_redis;
    }

    location /r/qisu {

        set_escape_uri $key "nginx_$uri";
        srcache_fetch GET /redis_get $key;
        srcache_store PUT /redis_set key=$key;

        proxy_pass http://backend_qisu;
        proxy_redirect    off;

        proxy_connect_timeout   60;
        proxy_send_timeout      60;
        proxy_read_timeout      60;

        proxy_buffering         on;
        proxy_buffer_size       8k;
        proxy_buffers           8 32k;
        proxy_busy_buffers_size 64k;

        proxy_headers_hash_bucket_size  64;
        proxy_headers_hash_max_size     512;

        proxy_ignore_client_abort       off;
        proxy_temp_file_write_size      64k;
        proxy_max_temp_file_size        0;
    }


Reference
==================================================
* http://blog.sina.com.cn/s/blog_6d579ff40100wi7p.html
* http://tengine.taobao.org/book/index.html>

