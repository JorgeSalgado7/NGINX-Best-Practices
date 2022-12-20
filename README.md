# NGINX Best Practices

### GZIP Compression
```sh
location / {

  ...Server configuration
  
  #GZIP Compression
  gzip		on;
  gzip_types	text/plain application/xml;
  gzip_proxied	no-cache no-store private expired auth;
  gzip_min_length	1000;
  
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
