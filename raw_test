**1st test:**  
`Using the raw module`

```sh
root@nms1:~/ansible# cat junos.hosts                                               
[all]                                                                              
vqfx1                                                                              
vqfx2                                                                              
root@nms1:~/ansible# ansible -i junos.hosts all -m raw -a "show version" -u jan -k 
SSH password:                                                                      
vqfx1 | SUCCESS | rc=0 >>                                                          
fpc0:                                                                              
--------------------------------------------------------------------------         
Hostname: vqfx1                                                                    
Model: vqfx-10000                                                                  
Junos: 15.1X53-D63.9                                                               
JUNOS Base OS boot [15.1X53-D63.9]                                                 
JUNOS Base OS Software Suite [15.1X53-D63.9]                                       
JUNOS Online Documentation [15.1X53-D63.9]                                         
JUNOS Crypto Software Suite [15.1X53-D63.9]                                        
JUNOS Packet Forwarding Engine Support (qfx-10-f) [15.1X53-D63.9]                  
JUNOS Kernel Software Suite [15.1X53-D63.9]                                        
JUNOS Web Management [15.1X53-D63.9]                                               
JUNOS Enterprise Software Suite [15.1X53-D63.9]                                    
JUNOS SDN Software Suite [15.1X53-D63.9]                                           
JUNOS Routing Software Suite [15.1X53-D63.9]                                       
JUNOS py-base-i386 [15.1X53-D63.9]                                                 
Shared connection to vqfx1 closed.                                                 
                                                                                   
                                                                                   
vqfx2 | SUCCESS | rc=0 >>                                                          
fpc0:                                                                              
--------------------------------------------------------------------------         
Hostname: vqfx2                                                                    
Model: vqfx-10000                                                                  
Junos: 15.1X53-D63.9                                                               
JUNOS Base OS boot [15.1X53-D63.9]                                                 
JUNOS Base OS Software Suite [15.1X53-D63.9]                                       
JUNOS Online Documentation [15.1X53-D63.9]                                         
JUNOS Crypto Software Suite [15.1X53-D63.9]                                        
JUNOS Packet Forwarding Engine Support (qfx-10-f) [15.1X53-D63.9]                  
JUNOS Kernel Software Suite [15.1X53-D63.9]                                        
JUNOS Web Management [15.1X53-D63.9]                                               
JUNOS Enterprise Software Suite [15.1X53-D63.9]                                    
JUNOS SDN Software Suite [15.1X53-D63.9]                                           
JUNOS Routing Software Suite [15.1X53-D63.9]                                       
JUNOS py-base-i386 [15.1X53-D63.9]                                                 
Shared connection to vqfx2 closed
```
