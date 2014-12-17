yumconf
=======

Role which helps to manage YUM configuration.


Examples
--------

```
---

# Example of how to use the role
- hosts: myhost
  roles:
    - role: yumconf
      # This configuration will disable GPG checking (gpgcheck=0)
      yumconf_conf:
        cachedir: /var/cache/yum/$basearch/$releasever
        debuglevel: 2
        distroverpkg: "{{ ansible_distribution | lower }}-release"
        exactarch: 1
        gpgcheck: 1
        installonly_limit: 5
        keepcache: 0
        logfile: /var/log/yum.log
        obsoletes: 1
        plugins: 1
        # This line will disable the GPG checking
        gpgcheck: 0
```


Role variables
--------------

List of variables used by the role:

```
# Default /etc/yum.conf configuration
yumconf_conf:
  # Name of the section
  main:
    # Parameters of the main section
    cachedir: /var/cache/yum/$basearch/$releasever
    debuglevel: 2
    distroverpkg: "{{ ansible_distribution | lower }}-release"
    exactarch: 1
    gpgcheck: 1
    installonly_limit: 5
    keepcache: 0
    logfile: /var/log/yum.log
    obsoletes: 1
    plugins: 1
```


License
-------

MIT


Author
------

Jiri Tyr
