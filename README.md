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
    - yumconf

# Example of how to change default value of one of the options
- hosts: myhost
  vars:
    # This configuration will disable GPG checking (gpgcheck=0)
    yumconf_config_main_gpgcheck: 0
  roles:
    - yumconf

# Example of how to add new option into the main section
- hosts: myhost
  vars:
    # This configuration will disable GPG checking (gpgcheck=0)
    yumconf_config_main__custom:
      proxy: http://my.proxy.com:1234
  roles:
    - yumconf

# Example of how to add new section
- hosts: myhost
  vars:
    # This configuration will disable GPG checking (gpgcheck=0)
    yumconf_config__custom:
      newsection:
        newoption: Hello
  roles:
    - yumconf
```


Role variables
--------------

List of variables used by the role:

```
# Path to the config file
yumconf_config_file: /etc/yum.conf

# Values of options in the main section
yumconf_config_main_cachedir: /var/cache/yum/$basearch/$releasever
yumconf_config_main_debuglevel: 2
yumconf_config_main_distroverpkg: "{{ ansible_distribution | lower }}-release"
yumconf_config_main_exactarch: 1
yumconf_config_main_gpgcheck: 1
yumconf_config_main_installonly_limit: 5
yumconf_config_main_keepcache: 0
yumconf_config_main_logfile: /var/log/yum.log
yumconf_config_main_obsoletes: 1
yumconf_config_main_plugins: 1

# Main section of the config
yumconf_config_main__default:
  # Parameters of the main section
  cachedir: "{{ yumconf_config_main_cachedir }}"
  debuglevel: "{{ yumconf_config_main_debuglevel }}"
  distroverpkg: "{{ yumconf_config_main_distroverpkg }}"
  exactarch: "{{ yumconf_config_main_exactarch }}"
  gpgcheck: "{{ yumconf_config_main_gpgcheck }}"
  installonly_limit: "{{ yumconf_config_main_installonly_limit }}"
  keepcache: "{{ yumconf_config_main_keepcache }}"
  logfile: "{{ yumconf_config_main_logfile }}"
  obsoletes: "{{ yumconf_config_main_obsoletes }}"
  plugins: "{{ yumconf_config_main_plugins }}"

# Custom options for the main section
yumconf_config_main__custom: {}

# Default /etc/yum.conf configuration
yumconf_config__default:
  # Name of the section
  main: "{{ yumconf_config_main__default }}{{  }}"

# Custom configuration
yumconf_config__custom: {}

# Final configuration
yumconf_config: "{{
  yumconf_conf__default.update(yumconf_conf__custom) }}{{
  yumconf_conf__default
}}"
```


License
-------

MIT


Author
------

Jiri Tyr
