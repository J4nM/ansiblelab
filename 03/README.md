# Homework #3

# Goal
## Create configuration files to deploy BGP peering between two Juniper vQFX
* Keep general, common and site specific data separate in group_vars.  
* Have all node/service specific data in element specific files in host_vars.
* Create separate files for each part and then join them in a final configuration file.
* Try out some Jinja2 features like default values, if-else conditions and loops.

# Building blocks
## group_vars

* [group_vars/all.yaml](https://github.com/J4nM/ansiblelab/blob/master/03/group_vars/all.yaml)
* [group_vars/lab.yaml](https://github.com/J4nM/ansiblelab/blob/master/03/group_vars/lab.yaml)

## host_vars

* [host_vars/vqfx1.yaml](https://github.com/J4nM/ansiblelab/blob/master/03/host_vars/vqfx1.yaml)
* [host_vars/vqfx2.yaml](https://github.com/J4nM/ansiblelab/blob/master/03/host_vars/vqfx2.yaml)

## Roles

* [roles/common/templates/base.conf.j2](https://github.com/J4nM/ansiblelab/blob/master/03/roles/common/templates/base.conf.j2)
* [roles/qfx/templates/vqfx.conf.j2](https://github.com/J4nM/ansiblelab/blob/master/03/roles/qfx/templates/vqfx.conf.j2)

## File layout

```
├── ansible.cfg
├── configs						#Destination for building parts and final result.
│   ├── vqfx1
│   │   ├── junos.conf
│   │   └── tmp
│   │       ├── base.conf.part
│   │       └── vqfx.conf.part
│   └── vqfx2
│       ├── junos.conf
│       └── tmp
│           ├── base.conf.part
│           └── vqfx.conf.part
├── group_vars									
│   ├── all.yaml					#Common data.
│   └── lab.yaml					#Site specific data.
├── host_vars						#Host specific data.
│   ├── vqfx1.yaml
│   └── vqfx2.yaml
├── juniper.inv
├── make_config.pb.yaml					#Playbook to create configurations.
└── roles
    ├── common
    │   ├── tasks
    │   │   └── main.yaml
    │   └── templates
    │       └── base.conf.j2				#Jinja2 template for common part.
    └── qfx
        ├── tasks
        │   └── main.yaml
        └── templates
            └── vqfx.conf.j2				#Jinja2 template for element specific part.
```

## Playbook
* [make_config.pb.yaml](https://github.com/J4nM/ansiblelab/blob/master/03/make_config.pb.yaml)

## Example play

```
# ansible-playbook make_config.pb.yaml 

PLAY [Build Juniper vQFX configs with jinja2 templates.] *********************************************************************

TASK [Delete directory if exists.] *******************************************************************************************
changed: [vqfx1 -> localhost]

TASK [Recreate empty directory.] *********************************************************************************************
changed: [vqfx1 -> localhost]

TASK [Create directory for each element.] ************************************************************************************
changed: [vqfx1]
changed: [vqfx2]

TASK [Create tmp output directory for each element.] *************************************************************************
changed: [vqfx1]
changed: [vqfx2]

PLAY [Create vQFX configuration from specified roles.] ***********************************************************************

TASK [common : Building base part] *******************************************************************************************
changed: [vqfx2]
changed: [vqfx1]

TASK [qfx : Building vqfx specific things...] ********************************************************************************
changed: [vqfx1]
changed: [vqfx2]

PLAY [Concatenate the configuration] *****************************************************************************************

TASK [assembling configfurations] ********************************************************************************************
changed: [vqfx2]
changed: [vqfx1]

PLAY RECAP *******************************************************************************************************************
vqfx1                      : ok=7    changed=7    unreachable=0    failed=0   
vqfx2                      : ok=5    changed=5    unreachable=0    failed=0   
```

# Example result

* [configs/vqfx1/junos.conf](https://github.com/J4nM/ansiblelab/blob/master/03/configs/vqfx1/junos.conf)
* [partly results](https://github.com/J4nM/ansiblelab/tree/master/03/configs/vqfx1/tmp)


