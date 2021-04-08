# Jitsi Meet docker-compose
The aim of this role is to set up a Jitsi Meet server very close to the published docker-compose [releases](https://github.com/jitsi/docker-jitsi-meet/releases) from the maintainers.

This role provides some default configurations to optimize data-protection. Check the defaults variables in `./defaults/main.yml` and the operations in task `./tasks/custom.yml`

Updated configuration files:

* `web/config.js`
* `web/interface_config.js`
* `jvb/logging.properties`