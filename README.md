# NGINX Best Practices

### GZIP Compression
```sh
server {

        #GZIP Compression
        gzip on;
        gzip_disable "msie6";
        gzip_comp_level 6;
        gzip_min_length 0;
        gzip_proxied any;
        gzip_buffers 16 8k;
        gzip_http_version 1.1;
        gzip_vary on;
        gzip_disable "msie6";
  
        gzip_types application/atom+xml application/geo+json
        application/javascript application/x-javascript application/json application/ld+json application/manifest+json
        application/rdf+xml application/rss+xml application/vnd.ms-fontobject application/wasm application/x-web-app-manifest+json
        application/xhtml+xml application/xml font/eot font/otf font/ttf image/bmp image/svg+xml text/cache-manifest text/calendar text/css
        text/javascript text/markdown text/plain text/xml text/vcard text/vnd.rim.location.xloc text/vtt text/x-component text/x-cross-domain-policy;

        location / {
          ...Server configuration
        }
  
} 
```

### Cache Control
```sh
#Cache Control
location ~* \.(js|css|png|jpg|jpeg|gif|svg|ico)$ {
  expires 31536000s;
  add_header Cache-Control "public, no-transform";
}

location ~* \.(jpg|jpeg|gif|png|svg)$ {
  expires 365d;
}

location ~* \.(pdf|css|html|js|swf)$ {
  expires 2d;
}

```
