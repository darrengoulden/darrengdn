---
layout: post
title:  "VMR Portal"
date:   2020-09-07 08:00:00 +0100
categories: pexip
tags: pexip vmrportal
comments: true
sitemap: true
---

500 LDAP Connection Error
Sorry, an unexpected error occured. Contact your system administrator if this problem persists.

Invalid Credentials

You can login but you don't see any meeting rooms
    In your LDAP sync source Utilities > LDAP Sync Template > LDAP-Sync > VMR/Device owner's email address

Failed to load virtual meeting room data from the API
    Check the docker logs `journalctl -fu docker.service`
    - Failed to establish a new connection: [Errno 113] Host is unreachable

    `openssl s_client -showcerts -connect pexipmgr.domain.com:443`

    You can get inside the container using `sudo docker exec -it vmrportal /bin/sh` to see if you have access to pexipmgr.domain.com from there (the same "ping" and "openssl" tests as before).    

Replacing the certificate
 - Check `systemctl status nginx.service`

 - Starting A high performance web server and a reverse proxy server...
   Enter PEM pass phrase:
   ...
   Failed to start A high performance web server and a reverse proxy server.

either remove the encryption for the private key;
openssl rsa -in your.key -out your.open.key
Or configure nginx to read a separate file for the key;
https://www.nginx.com/blog/secure-distribution-ssl-private-keys-nginx/#encrypt-keys