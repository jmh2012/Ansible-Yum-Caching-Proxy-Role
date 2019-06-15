# Yum Repo Caching Proxy Ansible Role

This role is used to set up a yum caching proxy server. 

Clients can configure yum to the proxy by adding the proxy option under the [main] section of /etc/yum.conf (using default squid port 3128):
```
[main]
...
proxy=http://<servername>:3128/
```

Repo files in /etc/yum.repos.d should be using a single baseurl instead of a mirrorlist, if you would rather use a mirrorlist the yum fastest mirror plugin should be disabled on clients since it might result in more cache misses.
In /etc/yum/pluginconf.d/fastestmirror.conf set:
```
enabled=0
```
then run:
```
yum clean all
```

In the group_vars of your playbook, you'll need to set localnetwork_allow to the subnet of the network which you'll allow access to the proxy.
