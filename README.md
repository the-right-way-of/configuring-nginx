## Configuring NGINX

### What's location?

The prime directive, its a conditional which works via regex matching for requests.

### Why is if wrong?

There's nothing wrong with `if`. Infact the fundamentals of this server are based on that.
The only problem is, countless hours are wasted in order to make it work. If you can make it work, its extremely hard to change.

### How does logging work?

The same way as any other system's logs work. You can choose between files, tty, stdout/stderr etc.
In docker world, the files have been mapped to stdout/stderr. If you need to disable any logs, just do `access_log off;`
This thing works like override inside location.

### Reverse proxy configuration?

There is much debate on `proxy_pass` and/or `proxy_redirect`. `proxy_redirect` is a bad choice. If you can stay away, do it as much as you can.
Try to pass `X-*` headers and see if they work. `X-Forwarded-For`, `X-Forwarded-Proto` etc are quite useful and they may avoid the need to use `proxy_redirect`.
Always utilize `upstream`, you can thank me later.
Utilize `keepalive` and `proxy_http_version` combination for extreme performances servers using HTTP1.1 and above. They don't make/break connections much.

#### What if nginx is in the middle of a reverse proxy and a server?
TBD

### Gzipping?

Bad idea where you have bandwidth available. Gzipping is good where internet connection of your peers is limited.
