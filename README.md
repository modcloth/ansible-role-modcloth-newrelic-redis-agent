modcloth.newrelic_redis_agent
=========

This role installs and configures the New Relic Redis agent
[https://github.com/modcloth/newrelic_redis_plugin](https://github.com/modcloth/newrelic_redis_plugin)

Requirements
------------

Ruby should be installed.

Role Variables
--------------
```yml
new_relic_license_key: # license key
newrelic_redis_agent_version: # version of the agent to install
newrelic_redis_agent_binary_path: # path to put the binary

newrelic_redis_agent_conf_path: # where to put the template
newrelic_redis_agent_template: # template to use for configuration (use "" to skip template writing)

# the default template uses the following variables:

newrelic_redis_agent_verbose: # 1 for verbose output, 0 for no
# list of redis to monitor
newrelic_redis_agent_agents: []
# each agent should be a dict with the following attributes:
# uri (required): URI of the redis instance to monitor (including the 'redis://' and port)
# instance_name (optional): Name to give the instance in New Relic (defaults to the hostname:port from the URI)
# database (optional): Database to monitor (get addition statistics -- this should typically be db0)
```

Dependencies
------------

None.

Example Playbook
----------------

```yml
---
- hosts: all
  roles:
  - role: modcloth.newrelic_redis_agent
    new_relic_license_key: 'ABC'
    newrelic_redis_agent_agents:
    - uri: 'redis://localhost:6379'
```

License
-------

MIT

Author Information
------------------

ModCloth, Inc.
