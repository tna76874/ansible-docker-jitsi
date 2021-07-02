# Jitsi Meet docker-compose
The aim of this role is to set up a Jitsi Meet server very close to the published docker-compose [releases](https://github.com/jitsi/docker-jitsi-meet/releases) from the maintainers.

Please note, that not every docker jitsi release seems to be really stable. Latest recommended release is: stable-5963

This role provides some default configurations to optimize data-protection and performance. Check the defaults variables in `./defaults/main.yml` and the operations in task `./tasks/custom.yml`

Updated configuration files:

* `web/config.js`
* `web/interface_config.js`
* `jvb/logging.properties`

#### Example playbook:

```bash
- name: Deploy jitsi server
  hosts: 
    - all
  become: yes
  vars:
    # Leave jitsi_docker_release blank to use latest jitsi release
  	jitsi_docker_release:
    nginx_domain_name: 'jitsi.mydomain.xyz'
    jitsi_username: 'adminuser'
    jitsi_password: 'supersecret'
    # place in 'files' folder in root folder
    config_logo_file: 'mypersonalwatermark.svg'
    config_unnamed_user: 'Fellow Jitster'
    config_name: 'Jitsi Meet'
    config_optimal_browsers: '[ ''chrome'', ''chromium'', ''nwjs'', ''electron'' ]'
    config_unsupported_browsers: '[ ''safari'', ''firefox'' ]'
    config_support_url: 'https://community.jitsi.org/'
    ## these configs can be deleted if used with an reverse proxy.
    reverse_proxy_setup: false
    config_tcp_port: 80
    config_tcp_port_https: 443
    config_enable_letsencrypt: 1
  roles:
    - tna76874.ansible_docker_jitsi
```

