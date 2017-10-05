README
===================



## 1. Saving router configurations to file.


```shell
# ansible-playbook report1.yaml 

PLAY [Retrieve configuration from Junos devices] ********************************************************************************************************************************

TASK [Retrieve configuration from Junos devices] ********************************************************************************************************************************
changed: [vqfx2]
changed: [vqfx1]

PLAY RECAP **********************************************************************************************************************************************************************
vqfx1                      : ok=1    changed=1    unreachable=0    failed=0   
vqfx2                      : ok=1    changed=1    unreachable=0    failed=0   

root@nms1:~/ansible# ll configs/
total 16
drwxr-xr-x 2 root root 4096 Oct  5 11:24 ./
drwxr-xr-x 8 root root 4096 Oct  5 11:24 ../
-rw-r--r-- 1 root root 3370 Oct  5 11:24 vqfx1.conf
-rw-r--r-- 1 root root 3326 Oct  5 11:24 vqfx2.conf
```

## 2. Saving router configurations to file is set command style.

```shell
# ansible-playbook report2.yaml  

PLAY [junos_facts module] *******************************************************************************************************************************************************

TASK [Collect facts and configurion in text on device] **************************************************************************************************************************
ok: [vqfx1]
ok: [vqfx2]

TASK [Save configuration to file in local directory] ****************************************************************************************************************************
changed: [vqfx1]
changed: [vqfx2]

PLAY RECAP **********************************************************************************************************************************************************************
vqfx1                      : ok=2    changed=1    unreachable=0    failed=0   
vqfx2                      : ok=2    changed=1    unreachable=0    failed=0   

root@nms1:~/ansible# ll configs/                   
total 24
drwxr-xr-x 2 root root 4096 Oct  5 11:25 ./
drwxr-xr-x 8 root root 4096 Oct  5 11:24 ../
-rw-r--r-- 1 root root 3370 Oct  5 11:24 vqfx1.conf
-rw-r--r-- 1 root root 2891 Oct  5 11:25 vqfx1.set.conf
-rw-r--r-- 1 root root 3326 Oct  5 11:24 vqfx2.conf
-rw-r--r-- 1 root root 2857 Oct  5 11:25 vqfx2.set.conf
```

## 3. Find out if NTP is configured on a device and if not record which device in a file.


```shell
# ansible-playbook report3.yaml  

PLAY [Check if NTP is configured and store all not devices configured in a file.] ***********************************************************************************************

TASK [Delete directory if exists.] **********************************************************************************************************************************************
changed: [vqfx2 -> localhost]

TASK [Recreate empty directory.] ************************************************************************************************************************************************
changed: [vqfx2 -> localhost]

TASK [Create an empty file.] ****************************************************************************************************************************************************
changed: [vqfx2]

TASK [show ntp status] **********************************************************************************************************************************************************
ok: [vqfx1]
ok: [vqfx2]

TASK [Add to file if no status.] ************************************************************************************************************************************************
skipping: [vqfx1]
changed: [vqfx2]

PLAY RECAP **********************************************************************************************************************************************************************
vqfx1                      : ok=1    changed=0    unreachable=0    failed=0   
vqfx2                      : ok=5    changed=4    unreachable=0    failed=0

# grep ntp configs/*set*
configs/vqfx1.set.conf:set system ntp server 192.168.1.4
```
