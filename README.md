# PROTO.ENRUTAMIENTO

## Configuración de Router

Para ingresar al modo privilegiado:

    >enable

    >ena

Para ingresar al modo de configuración:

    #configure terminal

    #conf t

Para ingresar a una interfaz (FastEthernet):

    #(config-if)interface FastEthernet 0/0
    
Para ingresar a una interfaz (GigabitEthernet):

    #(config-if)ip add IPv4 Mascara-Red

Para añadir una ip a esa interfaz:

    #(config-if)ip add IPv4 Mascara-Red

Siempre guardamos la configuración de un terminal

    #(config-if)no shutdown

Para salir de la interfaz:

    #(config-if)exit

Para ver las IPs de las interfaces:

    #show ip interface brief

