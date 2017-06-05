sa-lets-encrypt
===============

[![Build Status](https://travis-ci.org/softasap/sa-lets-encrypt.svg?branch=master)](https://travis-ci.org/softasap/sa-lets-encrypt)

This role is based on beautiful script https://github.com/lukas2511/dehydrated

Basic usage example:
<pre>
---
- hosts: dev

  vars:
    - root_dir: "{{ playbook_dir }}"
    - my_domains:
      - {
          names:        "voronenko.net www.voronenko.net",
          nginx_config: "/etc/nginx/sites-available/voronenko_net"
        }

  pre_tasks:
    - debug: msg="Pre tasks section"

  roles:
    - {
        role:              "sa-lets-encrypt",
        le_domains:        "{{ my_domains }}",
        option_run_once:   True,
        option_setup_cron: True
      }

  tasks:
    - debug: msg="Tasks section"
</pre>

Advanced example:
<pre>
---
- hosts: www

  vars:
    - root_dir: "{{ playbook_dir }}"
    - my_domains:
      - {
          names:        "voronenko.net www.voronenko.net",
          nginx_config: "/etc/nginx/sites-available/voronenko_net"
        }

  pre_tasks:
    - debug: msg="Pre tasks section"

  roles:
    - {
        role: "sa-nginx"
      }
    - {
        role:         "sa-include",
        include_file: "{{ root_dir }}/demosite.yml"
      }
    - {
        role:              "sa-lets-encrypt",
        le_domains:        "{{ my_domains }}",
        #le_ca:            "https://acme-staging.api.letsencrypt.org/directory",
        option_run_once:   True,
        option_setup_cron: True
      }

  tasks:
    - debug: msg="Tasks section"
</pre>

See standalone example in box-example folder.

![](https://raw.github.com/softasap/sa-lets-encrypt/master/box-example/docs/1.png)

![](https://raw.github.com/softasap/sa-lets-encrypt/master/box-example/docs/2.png)

![](https://raw.github.com/softasap/sa-lets-encrypt/master/box-example/docs/3.png)

![](https://raw.github.com/softasap/sa-lets-encrypt/master/box-example/docs/4.png)

![](https://raw.github.com/softasap/sa-lets-encrypt/master/box-example/docs/5.png)

![](https://raw.github.com/softasap/sa-lets-encrypt/master/box-example/docs/6.png)

![](https://raw.github.com/softasap/sa-lets-encrypt/master/box-example/docs/7.png)

![](https://raw.github.com/softasap/sa-lets-encrypt/master/box-example/docs/8.png)

![](https://raw.github.com/softasap/sa-lets-encrypt/master/box-example/docs/9.png)
