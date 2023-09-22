# PROTO.ENRUTAMIENTO-Router

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

Sin embargo, si queremos borrar la ruta estática que habíamos puesto en el router, colocamos (no ip route):

        (config)# no ip route 192.168.1.0 255.255.255.0 10.10.1.1

## DHCP

Primero creamos una regla para excluir las IPs, mediante un rango, que no queremos que el DHCP asigne a los dispositivos: 

    (config)# ip dhcp excluded-address (IP INICIAL DE LA RED QUE QUIERES EXCLUIR) (IP FINAL HASTA DONDE QUIERAS EXCLUIR)

Por ejemplo (excluimos del 1 al 10 para que no asigne a nadie):

    (config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10

Luego creamos el pool de direcciones disponibles a ser asignadas

    (config)# ip dhcp pool RED_LAN (cualquier nombre en vez de RED_LAN)

Posteriormente, le indicamos el network o red en la que el dhcp asignará IPs

    (dhcp-config)# network (DIRECCION-DE-RED) (MASCARA-DE-RED)

Luego le indicamos al router que el gateway predeterminado para los clientes DHCP en el pool RED_LAN, si no el router no sabría a que interfaz (gateway) realizaría DHCP

    (dhcp-config)# default router (IP DE LA INTERFAZ DE ROUTER DONDE SE ENCUENTRAN LOS CLIENTES DHCP)

    (dhcp-config)# default router 192.168.1.1

## MOSTRAR TABLA DE ENRUTAMIENTO DE UN ROUTER
La tabla de enrutamiento contiene información sobre las redes a las que el router puede llegar, así como la ruta que debe seguir para llegar a esas redes.

    #show ip route

## Mostrar Direcciones IP DHCP asigandos

se utiliza para mostrar las direcciones IP DHCP asignadas a los clientes DHCP en un router.

    #show ip dhcp binding

## Mostrar estado del pool de IPs del router

    #show ip dhcp pool

## OSPFV2
Configuración para que cada interface en el router hable OSPFV2:

    router ospf 1
    router-id 10.1.1.1
    interface FastEthernet0/0
    ip ospf 1 area 0




    
     



        

