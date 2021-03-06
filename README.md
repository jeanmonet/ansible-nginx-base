rixx.nginx-base
===============

A role to install nginx, including sensibly secure configuration according to latest Mozilla guidelines, and an UFW
rule. Works with Debian, Ubuntu, and Arch Linux.


Role Variables
--------------

- ``mozilla_configuration: modern|intermediate|old`` (default: ``modern``). This is one of the three possible Mozilla recommendated SSL configuration levels, as can be seen here (including
compatible systems): https://statics.tls.security.mozilla.org/server-side-tls-conf.json
- ``nginx_user: http``: This variable is OS specific and defined in vars/$os.yml
- ``nginx_dhparams_path: /etc/ssl/nginx.dhparams``
- ``nginx_dhparams_size: 4096``
- ``nginx_hsts: false``: Set to ``true`` to enable HSTS.
- ``nginx_hsts_age: 15768000``: Set HSTS protection age in seconds.
- ``nginx_sites_path: /etc/nginx/sites``
- ``nginx_worker_processes: false``: Set to ``true`` to enable auto worker processes.
- ``nginx_global_custom``: A string to be included on the uppermost config level, next to the ``http`` directive.
- ``nginx_acme_challenge: true``: Provide an acme challenge configuration, when nginx_base_conf in deployed.
- ``nginx_acme_challenge_path: /usr/share/nginx/letsencrypt``: Poing acme challenges here.
- ``nginx_acme_redirect: true``: Redirect to another server on incoming acme challenges. Mutually exclusive with ``nginx_acme_challenge``
- ``nginx_ufw_path: /etc/ufw/applications.d``: The ufw application config path
- ``nginx_base_conf: true``: apply template/nginx-base.conf with redirect to https etc..

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: rixx.ansible-base, x: 42 }

License
-------

BSD

Author Information
------------------

rixx <r at rixx.de>
