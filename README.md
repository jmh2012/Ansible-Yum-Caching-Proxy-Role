# Ansible Yum Repo Caching Proxy Role

This role is used to set up a yum caching proxy server. 

Clients can connect to the server with a .repo file such as this (using default squid port 3128):
```
[cache-repo]
proxy=http://<servername>:3128
gpgcheck=1
<any other needed yum repo options>
```

## To Do
Make repo sources on the proxy configurable via vars/templates
