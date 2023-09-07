# PROTO.ENRUTAMIENTO

## Configuración de Router

Para ingresar al modo privilegiado:

    >enable

    >ena

Para ingresar al modo de configuración:

    #configure terminal

    #conf t

Para ingresar a una interfaz (FastEthernet):

    (config-if)#interface FastEthernet 0/0
    
Para ingresar a una interfaz (GigabitEthernet):

    (config-if)#ip add IPv4 Mascara-Red

Para añadir una ip a esa interfaz:

    (config-if)#ip add IPv4 Mascara-Red

Siempre guardamos la configuración de un terminal

    (config-if)#no shutdown

Para salir de la interfaz:

    (config-if)#exit

Para ver las IPs de las interfaces:

    #show ip interface brief

## Enrutamiento estático (IP Route)

Es un tipo de enrutamiento que tiene una sola dirección en la que se envían los paquetes (no cambia). Lo malo de este tipo de enrutamiento es que si una red cae, entonces las demás redes que solían pasar por esa red para llegar a esa red ya no podrían pasar por ahí, por lo tanto no habría conexión entre esas redes.

    (config)# ip route (DIRECCION-DE-RED-POR-CONOCER) (MASCARA-DE-RED-POR-CONOCER) (IP-POR-DONDE-PASARA)

Por ejemplo:

    (config)# ip route 192.168.1.0 255.255.255.0 10.10.1.1

## DHCP

Primero creamos una regla para excluir las IPs, mediante un rango, que no queremos que el DHCP asigne a los dispositivos: 

    (config)# ip dhcp excluded-address (IP INICIAL DE LA RED QUE QUIERES EXCLUIR) (IP FINAL HASTA DONDE QUIERAS EXCLUIR)

Por ejemplo (excluimos del 1 al 10 para que no asigne a nadie):

    (config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10
     



        

