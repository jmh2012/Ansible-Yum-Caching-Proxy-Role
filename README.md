# Yum Repo Caching Proxy Ansible Role

This role is used to set up a yum caching proxy server. 

Clients can configure yum to the proxy by adding the proxy option under the [main] section of /etc/yum.conf (using default squid port 3128):
```
[main]
...
proxy=http://<servername>:3128/
```

The yum fastest mirror plugin should also be disabled on clients so that the proxy doesn't need to cache rpms from multiple sources.
In /etc/yum/pluginconf.d/fastestmirror.conf set:
```
enabled=0
```
then run:
```
yum clean all
```

In the group_vars of your playbook, you'll need to set localnetwork_allow to the subnet of the network which you'll allow access to the proxy.
