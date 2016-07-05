sa-lets-encrypt
===============

[![Build Status](https://travis-ci.org/softasap/sa-lets-encrypt.svg?branch=master)](https://travis-ci.org/softasap/sa-lets-encrypt)

Is based on beautiful script https://github.com/lukas2511/letsencrypt.sh

Example of use:

- hosts: dev

  pre_tasks:
    - debug: msg="Pre tasks section"

  roles:

    - {
        role: "sa-lets-encrypt"
      }


  tasks:
    - debug: msg="Tasks section"



Possible overrides:
