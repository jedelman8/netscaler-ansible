
# Ansible Modules for Netscaler Nitro API
You need to perform **two** steps to start using these modules.

1. Ensure this repository is in your Ansible module search path.
2. Install Dependencies.

## Ensure Modules are you in your search path
First, understand what your search path is:

```
$ ansible --version
ansible 2.1.1.0
  config file = /etc/ansible/ansible.cfg
  configured module search path = ???
```

If you already have a search path configured, clone the repo (see options below) while you are in your search path.

If you have a "default" or No search path shown, open the config file that is shown in the output above, here that is `/etc/ansible/ansible.cfg`.  In that file, you'll see these first few lines:

```
[defaults]

# some basic default values...

inventory      = /etc/ansible/hosts
library        = /home/ntc/projects/
```

Add a path for `library` - this will become your search path. Validate it with `ansible --version` after you make the change.

When you clone, do not forget to use `--recursive `!

**Option 1:**
```
$ git clone https://github.com/networktocode/netscaler-ansible --recursive
```

**Option 2:**
```
$ git clone https://github.com/networktocode/netscaler-ansible
$ cd netscaler-ansible
$ git submodule update --init --recursive
```

As a quick test and sanity use `ansible-doc` on one of the modules before trying to use them in a playbook.  For example, try this:
```
$ ansible-doc netscaler_save_config
```

If that works, Ansible can find the modules and you can proceed to installing the dependcies below.

## Install Dependencies
```
$ cd netscaler-ansible
$ pip install -r requirements.txt
```

## Modules
* **netscaler_server**
  + Used to create, update, and delete server objects. 
  + Returns the existing configuration for the server object and the configuration sent to the Netscaler API.
* **netscaler_servicegroup**
  + Used to create, update, and delete service group objects.
  + Returns the existing configuration for the service group and the configuration sent to the Netscaler API.
* **netscaler_lbvserver**
  + Used to create, update, and delete lb vserver objects.
  + Returns the existing configuration for the lb vserver and the configuration sent to the Netscaler API.
* **netscaler_lbmonitor**
  + Used to create, update, and delete lb monitor objects.
  + Returns the existing configuration for the lb monitor and the configuration sent to the Netscaler API.
* **netscaler_servicegroup_server**
  + Used to create and delete service group to server bindings. 
  + Returns all existing server objects bound to the service group, the existing configuration for the particular service group to server pair, and the configuration sent to the Netscaler API. 
* **netscaler_servicegroup_monitor**
  + Used to create and delete service group to lb monitor bindings. 
  + Returns all existing lb monitors bound to the service group, the existing configuration for the particular service group to lb monitor pair, and the configuration sent to the Netscaler API. 
* **netscaler_lbvserver_servicegroup**
  + Used to create and delete lb vserver to service group bindings. 
  + Returns all existing service groups bound to the lb vserver, the existing configuration for the particular lb vserver to service group pair, and the configuration sent to the Netscaler API. 
* **netscaler_lbvserver_certkey**
  + Used to create, update, and delete lb vserver to SSl cert key bindings. 
  + Returns all existing SSl cert keys bound to the lb vserver, the existing configuration for the particular lb vserver to SSL cert key pair, and the configuration sent to the Netscaler API. 
* **netscaler_facts**
  + Used to gather facts about the Netscaler system and configuration.
  + Returns system and hardware info, cli configuration, and json configurations for servers, service groups, lb vservers, and lb monitors.
* **netscaler_save_config**
  + Used to save the running configuration on the Netscaler to the device.
  + Returns the status code of the API request to save the configuration.

## Examples
See [Examples](examples.md)

## Contributing
SEE [Contributing](contributing.md)