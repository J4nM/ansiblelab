**1st test:**  
`Using the raw module`

```sh
root@nms1:~/ansible# cat raw_test.inv
[left]                               
vqfx1                                
[right]                              
vqfx2                                
                                     
[all:vars]                           
ansible_user=jan                     
ansible_ssh_pass=abc123

root@nms1:~/ansible# ansible-playbook -i raw_test.inv raw_test.yaml                     
                                                                                        
PLAY [all] *****************************************************************************
                                                                                        
TASK [raw] *****************************************************************************
changed: [vqfx1]                                                                        
changed: [vqfx2]                                                                        
                                                                                        
TASK [debug] ***************************************************************************
ok: [vqfx2] => {                                                                        
    "show.stdout_lines": [                                                              
        "fpc0:",                                                                        
        "--------------------------------------------------------------------------",   
        "Hostname: vqfx2",                                                              
        "Model: vqfx-10000",                                                            
        "Junos: 15.1X53-D63.9",                                                         
        "JUNOS Base OS boot [15.1X53-D63.9]",                                           
        "JUNOS Base OS Software Suite [15.1X53-D63.9]",                                 
        "JUNOS Online Documentation [15.1X53-D63.9]",                                   
        "JUNOS Crypto Software Suite [15.1X53-D63.9]",                                  
        "JUNOS Packet Forwarding Engine Support (qfx-10-f) [15.1X53-D63.9]",            
        "JUNOS Kernel Software Suite [15.1X53-D63.9]",                                  
        "JUNOS Web Management [15.1X53-D63.9]",                                         
        "JUNOS Enterprise Software Suite [15.1X53-D63.9]",                              
        "JUNOS SDN Software Suite [15.1X53-D63.9]",                                     
        "JUNOS Routing Software Suite [15.1X53-D63.9]",                                 
        "JUNOS py-base-i386 [15.1X53-D63.9]"                                            
    ]                                                                                   
}                                                                                       
ok: [vqfx1] => {                                                                        
    "show.stdout_lines": [                                                              
        "fpc0:",                                                                        
        "--------------------------------------------------------------------------",   
        "Hostname: vqfx1",                                                              
        "Model: vqfx-10000",                                                            
        "Junos: 15.1X53-D63.9",                                                         
        "JUNOS Base OS boot [15.1X53-D63.9]",                                           
        "JUNOS Base OS Software Suite [15.1X53-D63.9]",                                 
        "JUNOS Online Documentation [15.1X53-D63.9]",                                   
        "JUNOS Crypto Software Suite [15.1X53-D63.9]",                                  
        "JUNOS Packet Forwarding Engine Support (qfx-10-f) [15.1X53-D63.9]",            
        "JUNOS Kernel Software Suite [15.1X53-D63.9]",                                  
        "JUNOS Web Management [15.1X53-D63.9]",                                         
        "JUNOS Enterprise Software Suite [15.1X53-D63.9]",                              
        "JUNOS SDN Software Suite [15.1X53-D63.9]",                                     
        "JUNOS Routing Software Suite [15.1X53-D63.9]",                                 
        "JUNOS py-base-i386 [15.1X53-D63.9]"                                            
    ]                                                                                   
}                                                                                       
 [WARNING]: Could not match supplied host pattern, ignoring: nxos                       
                                                                                        
                                                                                        
PLAY [nxos] ****************************************************************************
skipping: no hosts matched                                                              
                                                                                        
PLAY RECAP *****************************************************************************
vqfx1                      : ok=2    changed=1    unreachable=0    failed=0             
vqfx2                      : ok=2    changed=1    unreachable=0    failed=0             
```
