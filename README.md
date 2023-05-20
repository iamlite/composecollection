# composecollection

Useful Docker compose files that can be used with minimal to no setup




Adguard:
```
#                 _                           _     #
#        /\      | |                         | |    #
#       /  \   __| | __ _ _   _  __ _ _ __ __| |    # 
#      / /\ \ / _` |/ _` | | | |/ _` | '__/ _` |    #
#     / ____ \ (_| | (_| | |_| | (_| | | | (_| |    #
#    /_/    \_\__,_|\__, |\__,_|\__,_|_|  \__,_|    #
#                    __/ |                          #
#                   |___/                           #

version: "3.5"
services:
  adguardhome:
    image: adguard/adguardhome:latest
    container_name: adguardhome
    volumes:
    - /path/to/adguard/work:/opt/adguardhome/work # persistent data
    - /path/to/adguard/conf:/opt/adguardhome/conf # persistent config
    restart: unless-stopped
    networks:
      local_lan: # attach the container to the local_lan network
        ipv4_address: 000.000.000.000 # give it a static ip address
        ipv6_address: 0000:0000:0000::0000 # same but ipv6
        
networks: # create a network for the container
  local_lan: # name of the network
    name: local_lan 

```

DashDot:
```
#    _____            _     _____        _      #
#   |  __ \          | |   |  __ \      | |     #
#   | |  | | __ _ ___| |__ | |  | | ___ | |_    #
#   | |  | |/ _` / __| '_ \| |  | |/ _ \| __|   #
#   | |__| | (_| \__ \ | | | |__| | (_) | |_    #
#   |_____/ \__,_|___/_| |_|_____/ \___/ \__|   #
#                                               #                                       

version: '3.5'
services:  
  dash:    
    image: mauricenino/dashdot:latest
    container_name: dashdot
    restart: unless-stopped    
    privileged: true    
    ports:      
      - '8338:3001'    
    volumes:    
      - /:/mnt/host:ro   
    environment:      
      - DASHDOT_SHOW_HOST= 'true'      
      - DASHDOT_SHOW_DASH_VERSION= 'true'      
      - DASHDOT_ENABLE_CPU_TEMPS= 'true'      
      - DASHDOT_ALWAYS_SHOW_PERCENTAGES= 'true'
      
```