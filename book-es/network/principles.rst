.. Copyright |copy| 2010 by Olivier Bonaventure
.. This file is licensed under a `creative commons licence <http://creativecommons.org/licenses/by/3.0/>`_

.. Principles
Principios
##########

.. The main objective of the network layer is to allow endsystems, connected to different networks, to exchange information through intermediate systems called :term:`router`. The unit of information in the network layer is called a :term:`packet`.
El objetivo principal de la capa de Red es permitir a los sistemas finales, conectados a diferentes redes, intercambiar información mediante sistemas intermedios. Cada uno de estos sistemas intermedios recibe el nombre de :term:`router`. La unidad de información en la capa de Red se llama `paquete` (:term:`packet`).

.. figure:: svg/osi-network.png
   :align: center
   :scale: 80
  
   La capa de Red en el Modelo de Referencia 
..   The network layer in the reference model

.. Before explaining the network layer in detail, it is useful to begin by analysing the service provided by the `datalink` layer. There are many variants of the datalink layer. Some provide a connection-oriented service while others provide a connectionless service. In this section, we focus on connectionless datalink layer services as they are the most widely used. Using a connection-oriented datalink layer causes some problems that are beyond the scope of this chapter. See :rfc:`3819` for a discussion on this topic.

Antes de explicar la capa de Red en detalle, será útil comenzar analizando el servicio provisto por la capa de Enlace de datos. Existen numerosas variantes de la capa de Enlace de Datos. Algunas ofrecen un servicio orientado a conexión, mientras que otras, servicio sin conexión. En esta sección nos concentraremos en los servicios de capa de Enlace de Datos sin conexión, ya que son los más ampliamente usados. El uso de una capa de Enlace de Datos orientada a conexión causa algunos problemas que exceden el alcance de este capítulo. Véase en :rfc:`3819` una discusión sobre este asunto.

.. figure:: svg/osi-datalink.png
   :align: center
   :scale: 70   

   La capa de Enlace de Datos punto a punto
..   The point-to-point datalink layer

.. There are three main types of datalink layers. The simplest datalink layer is when there are only two communicating systems that are directly connected through the physical layer. Such a datalink layer is used when there is a point-to-point link between the two communicating systems. The two systems can be endsystems or routers. :abbr:`PPP (Point-to-Point Protocol)`, defined in :rfc:`1661`, is an example of such a point-to-point datalink layer. Datalink layers exchange `frames` and a datalink :term:`frame` sent by a datalink layer entity on the left is transmitted through the physical layer, so that it can reach the datalink layer entity on the right. Point-to-point datalink layers can either provide an unreliable service (frames can be corrupted or lost) or a reliable service (in this case, the datalink layer includes retransmission mechanisms similar to the ones used in the transport layer). The unreliable service is frequently used above physical layers (e.g. optical fiber, twisted pairs) having a low bit error ratio while reliability mechanisms are often used in wireless networks to recover locally from transmission errors.

Existen tres tipos principales de capas de enlace de datos. El más simple es aquel donde hay sólo dos sistemas que se comunican, directamente conectados a través de la capa física. Esta capa de enlace de datos se usa cuando hay un vínculo punto a punto (`point-to-point`) entre ambos sistemas. Los sistemas pueden ser sistemas finales o routers. El Protocolo Punto a Punto (`Point-to-Point Protocol`, :abbr:`PPP`), definido en :rfc:`1661`, es un ejemplo de dicha capa de Enlace de Datos punto a punto. La unidad de datos intercambiada por las entidades de capa de Enlace de Datos se denomina `trama` (:term:`frame`). Cada trama enviada por la entidad de Enlace de Datos a la izquierda es transmitida a través de la capa Física, de modo que llegue a la entidad de Enlace de Datos a la derecha. Las capas de Enlace de Datos punto a punto pueden ofrecer un servicio no confiable (las tramas pueden sufrir corrupción o pérdidad) o un servicio confiable (en este caso la capa de Enlace de Datos incluye mecanismos de retransmisión similares a los usados en la capa de Transporte). El servicio no confiable se usa frecuentemente sobre capas físicas que tienen baja tasa de errores de bits (`Bit Error Ratio`, o BER), como, por ejemplo, fibra óptica o pares retorcidos. Por el contrario, en redes inalámbricas, suelen usarse mecanismos de confiabilidad para recuperarse localmente de los errores de transmisión. 

.. The second type of datalink layer is the one used in Local Area Networks (LAN). Conceptually, a LAN is a set of communicating devices such that any two devices can directly exchange frames through the datalink layer. Both endsystems and routers can be connected to a LAN. Some LANs only connect a few devices, but there are LANs that can connect hundreds or even thousands of devices.

El segundo tipo de capa de Enlace de Datos es el usado en Redes de Área Local (`Local Area Networks`, LAN). Conceptualmente, una LAN es un conjunto de dispositivos que se comunican, de modo que dos dispositivos cualesquiera pueden intercambiar, directamente, tramas mediante la capa de Enlace de Datos. Una LAN puede interconectar tanto sistemas finales como routers. Algunas LANs sólo conectan unos pocos dispositivos, pero existen LANs que pueden conectar cientos o miles de dispositivos.

.. figure:: svg/simple-lan.png
   :align: center
   :scale: 80    
   
   Una red de área local
..   A local area network 

.. In the next chapter, we describe the organisation and the operation of Local Area Networks. An important difference between the point-to-point datalink layers and the datalink layers used in LANs is that in a LAN, each communicating device is identified by a unique `datalink layer address`. This address is usually embedded in the hardware of the device and different types of LANs use different types of datalink layer addresses. A communicating device attached to a LAN can send a datalink frame to any other communicating device that is attached to the same LAN. Most LANs also support special broadcast and multicast datalink layer addresses. A frame sent to the broadcast address of the LAN is delivered to all communicating devices that are attached to the LAN. The multicast addresses are used to identify groups of communicating devices. When a frame is sent towards a multicast datalink layer address, it is delivered by the LAN to all communicating devices that belong to the corresponding group.

En el próximo capítulo describiremos la organización y la operación de las Redes de Área Local. Una diferencia importante entre las capas de Enlace de Datos punto a punto y las usadas en LANs es que, en una LAN, cada dispositivo que se comunica es identificado por una `dirección de capa de Enlace de Datos` única. Esta dirección está típicamente incorporada en el hardware del dispositivo, y diferentes tipos de LANs usan diferentes tipos de direcciones de capa de Enlace de Datos. Un dispositivo conectado a una LAN puede enviar una trama de Enlace de Datos a cualquier otro dispositivo que esté conectado a la misma LAN. La mayoría de las LANs además soportan direcciones de Enlace de Datos especiales, de `broadcast` y de `multicast`. Una trama enviada a la dirección de `broadcast`, o de `difusión`, de la LAN es entregada a todos los dispositivos conectados a la LAN. Las direcciones de `multicast` se usan para identificar grupos de dispositivos que se comunican. Cuando se envía una trama a una dirección de Enlace de Datos de `multicast`, la trama es enviada por la LAN a todos los dispositivos que pertenecen al grupo correspondiente.

.. index:: NBMA, Non-Broadcast Multi-Access Networks

.. The third type of datalink layers are used in Non-Broadcast Multi-Access (NBMA) networks. These networks are used to interconnect devices like a LAN. All devices attached to an NBMA network are identified by a unique datalink layer address. However, and this is the main difference between an NBMA network and a traditional LAN, the NBMA service only supports unicast. The datalink layer service provided by an NBMA network supports neither broadcast nor multicast.

El tercer tipo de capa de enlace de datos se usa en `redes de acceso múltiple sin difusión` (`Non-Broadcast Multi-Access` networks, NBMA). Estas redes se usan para interconectar dispositivos como en una LAN. Todos los dispositivos conectados a la red NBMA se identifican con una dirección de capa de Enlace de Datos única. Sin embargo, y ésta es la principal diferencia entre una red NBMA y una LAN tradicional, el servicio NBMA sólo soporta `unicast`. El servicio de capa de Enlace de Datos provisto por una red NBMA no soporta `broadcast` ni `multicast`.

.. Unfortunately no datalink layer is able to send frames of unlimited side. Each datalink layer is characterised by a maximum frame size. There are more than a dozen different datalink layers and unfortunately most of them use a different maximum frame size. The network layer must cope with the heterogeneity of the datalink layer.

Desafortunadamente, ninguna capa de Enlace de Datos es capaz de enviar tramas de tamaño ilimitado. Cada capa de Enlace de Datos se caracteriza por un tamaño máximo de trama. Existe más de una docena de diferentes capas de Enlace, y por desgracia la mayoría de ellas usa un tamaño de trama diferente. La capa de Red es quien debe enfrentar el problema de la heterogeneidad de la capa de Enlace de Datos.

.. The network layer itself relies on the following principles : 
..  #. Each network layer entity is identified by a `network layer address`. This address is independent of the datalink layer addresses that it may use.
.. #. The service provided by the network layer does not depend on the service or the internal organisation of the underlying datalink layers.
.. #. The network layer is conceptually divided into two planes : the `data plane` and the `control plane`. The `data plane` contains the protocols and mechanisms that allow hosts and routers to exchange packets carrying user data. The `control plane` contains the protocols and mechanisms that enable routers to efficiently learn how to forward packets towards their final destination. 

La capa de Red, por su parte, se apoya en los siguientes principios:

 #. Cada entidad de capa de Red se identifica por una `dirección de capa de Red`. Esta dirección es independiente de las direcciones de capa de Enlace de Datos que pueda usar la entidad de Red. 
 #. El servicio provisto por la capa de Red no depende del servicio o de la organización interna de las capas de Enlace de Datos subyacentes.
 #. La capa de Red está conceptualmente dividida en dos planos: el `plano de datos` y el `plano de control`. 

    - El plano de datos contiene los protocolos y mecanismos que permiten a los `hosts y routers` intercambiar paquetes que transportan `datos de usuario`. 
    - El plano de control contiene los protocolos y mecanismos que permiten a los `routers` aprender eficientemente `cómo reenviar paquetes` hasta su destino final.


.. The independence of the network layer from the underlying datalink layer is a key principle of the network layer. It ensures that the network layer can be used to allow hosts attached to different types of datalink layers to exchange packets through intermediate routers. Furthermore, this allows the datalink layers and the network layer to evolve independently from each other. This enables the network layer to be easily adapted to a new datalink layer every time a new datalink layer is invented.

La independencia de la capa de Red de la capa de Enlace de Datos, subyacente, es un principio clave de la capa de Red. Asegura que, gracias a la capa de Red, hosts conectados a diferentes tipos de Enlace de Datos puedan intercambiar paquetes atravesando los routers intermedios. Además, esto permite que la capa de Enlace de Datos y la de Red evolucionen independientemente una de otra. Así, la capa de Red puede adaptarse fácilmente a cada nueva capa de Enlace de Datos que sea inventada.

.. There are two types of service that can be provided by the network layer :

.. - an `unreliable connectionless` service
.. - a `connection-oriented`, reliable or unreliable, service

Existen dos tipos de servicio que pueden ser provistos por la capa de Red:

 - Un servicio `sin conexión, no confiable`;
 - Un servicio `orientado a conexión`, confiable o no confiable.

.. Connection-oriented services have been popular with technologies such as :term:`X.25` and :term:`ATM` or :term:`frame-relay`, but nowadays most networks use an `unreliable connectionless` service. This is our main focus in this chapter.

Los servicios orientados a conexión han sido populares con tecnologías como :term:`X.25` y :term:`ATM` o :term:`frame-relay`, pero hoy en día la mayoría de las redes usan un servicio `sin conexión, no confiable`. Éste es el foco central de este capítulo.

.. Organisation of the network layer
Organización de la capa de Red
==============================

.. index:: datagram, virtual circuit

.. There are two possible internal organisations of the network layer : 

..  - datagram 
..  - virtual circuits 

Hay dos posibles organizaciones internas de la capa de Red: 

  - Datagramas
  - Circuitos Virtuales

.. The internal organisation of the network is orthogonal to the service that it provides, but most of the time a datagram organisation is used to provide a connectionless service while a virtual circuit organisation is used in networks that provide a connection-oriented service.

La organización interna de la red es ortogonal al servicio que provee, pero la mayoría de las veces, una organización de datagramas es usada para proveer un servicio sin conexión, mientras que una organización de circuitos virtuales se usa en las redes que ofrecen un servicio orientado a conexión.

.. Datagram organisation
Organización de datagramas
--------------------------

.. The first and most popular organisation of the network layer is the datagram organisation. This organisation is inspired by the organisation of the postal service. Each host is identified by a `network layer address`. To send information to a remote host, a host creates a packet that contains :

.. - the network layer address of the destination host
.. - its own network layer address
.. - the information to be sent

La primera y más popular organización de la capa de Red es la de datagramas. Esta organización está inspirada por la de un servicio postal tradicional. Cada host está identificado por una `dirección de capa de Red`. Para enviar información a un host remoto, un host crea un paquete que contiene:

 - La dirección de capa de Red del host destino;
 - Su propia dirección de capa de Red;
 - La información a ser enviada.

.. The network layer limits the maximum packet size. Thus, the information must have been divided in packets by the transport layer before being passed to the network layer. 

La capa de Red limita el tamaño máximo de los paquetes. Luego, la información debe ser dividida en paquetes por la capa de Transporte antes de ser pasada a la capa de Red.

.. To understand the datagram organisation, let us consider the figure below. A network layer address, represented by a letter, has been assigned to each host and router. To send some information to host `J`, host `A` creates a packet containing its own address, the destination address and the information to be exchanged.

Para comprender la organización de datagramas, consideremos la figura siguiente. Una dirección de capa de Red, representada por una letra, ha sido asignada a cada host y a cada router. Para enviar una información al host `J`, el host `A` crea un paquete conteniendo su propia dirección, la dirección destino y la información a ser intercambiada.

.. figure:: svg/simple-internetwork.png
   :align: center
   :scale: 80   

   Una `internetwork` simple
..   A simple internetwork 

.. index:: hop-by-hop forwarding

.. With the datagram organisation, routers use `hop-by-hop forwarding`. This means that when a router receives a packet that is not destined to itself, it looks up the destination address of the packet in its `routing table`. A `routing table` is a data structure that maps each destination address (or set of destination addresses) to the outgoing interface over which a packet destined to this address must be forwarded to reach its final destination. 

Con la organización de datagramas, los routers usan `reenvío salto por salto` (`hop-by-hop forwarding`). Esto significa que, cuando un router recibe un paquete que no está destinado a él, busca la dirección destino del paquete en su `tabla de ruteo`. Una `tabla de ruteo` es una estructura de datos que mapea cada dirección destino, o conjunto de ellas, a la interfaz de salida por la cual debe ser reenviado el paquete para alcanzar su destino final.

.. The main constraint imposed on the routing tables is that they must allow any host in the network to reach any other host. This implies that each router must know a route towards each destination, but also that the paths composed from the information stored in the routing tables must not contain loops. Otherwise, some destinations would be unreachable. 

La restricción principal impuesta sobre las tablas de ruteo es que deben permitir que cualquier host en la red pueda alcanzar a cualquier otro host. Esto implica que cada router debe conocer una ruta hacia cada uno de los demás destinos; pero también, que los caminos conformados por la información almacenada en las tablas de ruteo no deben contener ciclos. De lo contrario, algunos destinos se volverán inalcanzables.

.. In the example above, host `A` sends its packet to router `R1`. `R1` consults its routing table and forwards the packet towards `R2`. Based on its own routing table, `R2` decides to forward the packet to `R5` that can deliver it to its destination.

En el ejemplo anterior, el host `A` envía su paquete al router `R1`. `R1` consulta su tabla de ruteo y reenvía el paquete hacia `R2`. Basándose en su propia tabla de ruteo, `R2` decide reenviar el paquete a `R5`, quien puede entregarlo a su destinatario.

.. To allow hosts to exchange packets, a network relies on two different types of protocols and mechanisms. First, there must be a precise definition of the format of the packets that are sent by hosts and processed by routers. Second, the algorithm used by the routers to forward these packets must be defined. This protocol and this algorithm are part of the `data plane` of the network layer. The `data plane` contains all the protocols and algorithms that are used by hosts and routers to create and process the packets that contain user data.

Para permitir a los hosts intercambiar paquetes, una red se apoya en dos diferentes tipos de protocolos y mecanismos. En primer lugar, debe existir una definición precisa del formato de los paquetes que son enviados por los hosts y procesados por los routers. En segundo lugar, el algoritmo usado por los routers para reenviar estos paquetes debe estar definido. Este protocolo y este algoritmo son partes del `plano de datos` de la capa de Red. El `plano de datos` contiene todos los protocolos y algoritmos que son usados por los hosts y los routers para crear y procesar los paquetes que contienen datos de usuario.

.. The `data plane`, and in particular the forwarding algorithm used by the routers, depends on the routing tables that are maintained on reach router. These routing tables can be maintained by using various techniques (manual configuration, distributed protocols, centralised computation, etc). These techniques are part of the `control plane` of the network layer. The `control plane` contains all the protocols and mechanisms that are used to compute and install routing tables on the routers.

El `plano de datos`, y en particular el algoritmo de reenvío usado por los routers, depende de las tablas de ruteo que son mantenidas en cada router. Estas tablas de ruteo pueden ser mantenidas usando varias técnicas (configuración manual, protocolos distribuidos, cómputo centralizado, etc.). Estas técnicas son parte del `plano de control` de la capa de Red. El `plano de control` contiene todos los protocolos y mecanismos usados para computar e instalar las tablas de ruteo en los routers. 

.. The datagram organisation has been very popular in computer networks. Datagram based network layers include IPv4 and IPv6 in the global Internet, CLNP defined by the ISO, IPX defined by Novell or XNS defined by Xerox [Perlman2000]_.

La organización de datagramas ha sido muy popular en las redes de computadoras. Entre las capas de redes basadas en datagramas se encuentran IPv4 e IPv6 en la Internet global; CLNP, definida por ISO; IPX, definido por Novell, y XNS, definido por Xerox [Perlman2000]_.

.. Virtual circuit organisation
Organización de Circuitos Virtuales
-----------------------------------

.. The main advantage of the datagram organisation is its simplicity. The principles of this organisation can easily be understood. Furthermore, it allows a host to easily send a packet towards any destination at any time. However, as each packet is forwarded independently by intermediate routers, packets sent by a host may not follow the same path to reach a given destination. This may cause packet reordering, which may be annoying for transport protocols. Furthermore, as a router using `hop-by-hop forwarding` always forwards packets sent towards the same destination over the same outgoing interface, this may cause congestion over some links.

La principal ventaja de la organización de datagramas es su simplicidad: los principios de esta organización pueden ser fácilmente comprendidos, y permiten que un host envíe un paquete hacia cualquier destino, en cualquier momento y con facilidad. Sin embargo, como los paquetes son reenviados en forma independiente por los routers intermedios, aquellos paquetes que son enviados por un mismo host pueden no seguir el mismo camino para llegar a un destino dado. Esto puede causar el `reordenamiento` de los paquetes, cosa que puede resultar problemática para los protocolos de transporte. Por otro lado, como un router que realiza `reenvío salto por salto` siempre reenvía por la misma interfaz los paquetes enviados al mismo destino, esto puede causar congestión sobre algunos enlaces. 

.. The second organisation of the network layer, called `virtual circuits`, has been inspired by the organisation of telephone networks. Telephone networks have been designed to carry phone calls that usually last a few minutes. Each phone is identified by a telephone number and is attached to a telephone switch. To initiate a phone call, a telephone first needs to send the destination's phone number to its local switch. The switch cooperates with the other switches in the network to create a bi-directional channel between the two telephones through the network. This channel will be used by the two telephones during the lifetime of the call and will be released at the end of the call. Until the 1960s, most of these channels were created manually, by telephone operators, upon request of the caller. Today's telephone networks use automated switches and allow several channels to be carried over the same physical link, but the principles remain roughly the same.

La segunda forma de organización de la capa de Red, llamada de `Circuitos Virtuales`, ha sido inspirada por la organización de las redes telefónicas. Dichas redes han sido diseñadas para transportar llamadas telefónicas que duran normalmente unos pocos minutos. Cada dispositivo de comunicación se identifica por un número de teléfono, y está conectado a un conmutador telefónico. Para iniciar una llamada, un teléfono primeramente necesita enviar el número de teléfono destinatario a su conmutador local. El conmutador coopera con los demás conmutadores de la red para crear un canal bidireccional entre los dos teléfonos a través de la red. Hasta los años 60, la mayoría de estos canales eran creados manualmente, por operadores telefónicos, a demanda del originador de la llamada. Las redes telefónicas de hoy usan conmutadores (`switches`) automatizados, y permiten que varios canales sean conducidos sobre el mismo vínculo físico, pero los principios se conservan casi sin cambios.

.. In a network using virtual circuits, all hosts are identified with a network layer address. However, a host must explicitly request the establishment of a `virtual circuit` before being able to send packets to a destination host. The request to establish a virtual circuit is processed by the `control plane`, which installs state to create the virtual circuit between the source and the destination through intermediate routers. All the packets that are sent on the virtual circuit contain a virtual circuit identifier that allows the routers to determine to which virtual circuit each packet belongs. This is illustrated in the figure below with one virtual circuit between host `A` and host `I` and another one between host `A` and host `J`. 

En una red que usa circuitos virtuales, todos los hosts se identifican con una dirección de capa de Red. Sin embargo, un host debe requerir explícitamente el establecimiento de un `circuito virtual` antes de poder enviar paquetes a un host destino. La solicitud de establecer un circuito virtual es procesada por el `plano de control`, que instala `estado` para crear el circuito virtual entre origen y destino a través de routers intermedios. Todos los paquetes enviados por el circuito virtual contienen un identificador, que permite a los routers determinar a qué circuito virtual pertenece el paquete. Esto se ilustra en la figura siguiente con un circuito virtual entre los hosts `A` e `I`, y otro entre los hosts `A` y `J`. 

.. figure:: svg/simple-internetwork-vc.png
   :align: center
   :scale: 70   

   Una `internetwork` simple usando circuitos virtuales
..   A simple internetwork using virtual-circuits

				   
.. The establishment of a virtual circuit is performed using a `signalling protocol` in the `control plane`. Usually, the source host sends a signalling message to indicate to its router the address of the destination and possibly some performance characteristics of the virtual circuit to be established. The first router can process the signalling message in two different ways.

El establecimiento de un circuito virtual se realiza usando un `protocolo de señalización` en el `plano de control`. Normalmente, el host origen envía un mensaje de señalización para indicar a su router la dirección del destino, y posiblemente algunas características de performance del circuito virtual a establecer. El primer router puede procesar el mensaje de señalización en dos formas diferentes.

.. A first solution is for the router to consult its routing table, remember the characteristics of the requested virtual circuit and forward it over its outgoing interface towards the destination. The signalling message is thus forwarded hop-by-hop until it reaches the destination and the virtual circuit is opened along the path followed by the signalling message. This is illustrated with the red virtual circuit in the figure below.

Una primera forma es que el router consulte su tabla de ruteo, memorice las características del circuito virtual requerido y las reenvíe sobre su interfaz de salida hacia el destino. El mensaje de señalización entonces es reenviado de salto en salto hasta que llega al destino, y el circuito virtual queda abierto sobre el camino seguido por el mensaje de señalización. Esto se ilustra en la figura siguiente con el circuito virtual rojo.

.. figure:: svg/simple-internetwork-vc-estab.png
   :align: center
   :scale: 70   

   Establecimiento de circuito virtual
..   Virtual circuit establishment


.. index:: source routing, label

.. A second solution can be used if the routers know the entire topology of the network. In this case, the first router can use a technique called `source routing`. Upon reception of the signalling message, the first router chooses the path of the virtual circuit in the network. This path is encoded as the list of the addresses of all intermediate routers to reach the destination. It is included in the signalling message and intermediate routers can remove their address from the signalling message before forwarding it. This technique enables routers to spread the virtual circuits throughout the network better. If the routers know the load of remote links, they can also select the least loaded path when establishing a virtual circuit. This solution is illustrated with the blue circuit in the figure above.

Una segunda forma es la que puede usarse cuando los routers conocen la topología completa de la red. En este caso, el primer router puede usar una técnica llamada `ruteo por origen` (`source routing`). Al recibir el mensaje de señalización, el primer router elige el camino del circuito virtual en la red. Este camino se codifica como la lista de las direcciones de todos los routers que se interponen hasta llegar a destino. La lista se incluye en el mensaje de señalización, y los routers intermedios, a medida que reciben este mensaje, borran su propia dirección de la lista antes de reenviarlo al siguiente. Esta técnica permite a los routers distribuir mejor los circuitos virtuales por la red. Si los routers conocen la carga de los enlaces remotos, pueden también seleccionar el camino menos cargado al establecer un circuito virtual. Esta solución se ilustra en la figura anterior con el circuito azul.
	   
.. The last point to be discussed about the virtual circuit organisation is its `data plane`. The `data plane` mainly defines the format of the data packets and the algorithm used by routers to forward packets. The data packets contain a virtual circuit identifier, encoded as a fixed number of bits. These virtual circuit identifiers are usually called `labels`.

El último punto a discutir sobre la organización de circuitos virtuales es el `plano de datos`. El `plano de datos` define principalmente el formato de los paquetes de datos y algoritmos usados por los routers para reenviar paquetes. Los paquetes de datos contienen un identificador de circuito virtual, codificado con una cantidad fija de bits. Estos identificadores de vircuito virtual suelen ser llamados `rótulos` (`labels`).

.. Each host maintains a flow table that associates a label with each virtual circuit that is has established. When a router receives a packet containing a label, it extracts the label and consults its `label forwarding table`. This table is a data structure that maps each couple `(incoming interface, label)` to the outgoing interface to be used to forward the packet as well as the label that must be placed in the outgoing packets. In practice, the label forwarding table can be implemented as a vector and the couple `(incoming interface, label)` is the index of the entry in the vector that contains the outgoing interface and the outgoing label. Thus a single memory access is sufficient to consult the label forwarding table. The utilisation of the label forwarding table is illustrated in the figure below.

Cada host mantiene una tabla de flujo que asocia un rótulo con cada circuito virtual que ha establecido. Cuando un router recibe un paquete, extrae el rótulo y consulta su `tabla de reenvío de rótulos`. Esta tabla es una estructura de datos que mapea cada par `(interfaz de entrada, rótulo)` a la interfaz de salida que será usada para reenviar el paquete y al rótulo que será usado como identificador en los paquetes salientes. En la práctica, la tabla de reenvío de rótulos puede ser implementada como un vector, y la tupla `(interfaz de entrada, rótulo)` es el índice del elemento del vector que contiene la interfaz de salida y el rótulo de salida. Así es suficiente un único acceso a memoria para consultar la tabla de reenvío de rótulos. La utilización de la tabla de reenvío de rótulos se ilustra en la figura siguiente.

.. figure:: svg/label-forwarding.png
   :align: center
   :scale: 70   

   Tablas de reenvío de rótulos en una red que usa circuitos virtuales
..   Label forwarding tables in a network using virtual circuits

.. The virtual circuit organisation has been mainly used in public networks, starting from X.25 and then Frame Relay and Asynchronous Transfer Mode (ATM) network. 

La organización de circuitos virtuales ha sido usada principalmente en redes públicas, comenzando con X.25, luego Frame Relay, y más recientemente, las redes ATM (`Asynchronous Transfer Mode`). 

.. Both the datagram and virtual circuit organisations have advantages and drawbacks. The main advantage of the datagram organisation is that hosts can easily send packets to any number of destinations while the virtual circuit organisation requires the establishment of a virtual circuit before the transmission of a data packet. This solution can be costly for hosts that exchange small amounts of data. On the other hand, the main advantage of the virtual circuit organisation is that the forwarding algorithm used by routers is simpler than when using the datagram organisation. Furthermore, the utilisation of virtual circuits may allow the load to be better spread through the network thanks to the utilisation of multiple virtual circuits. The MultiProtocol Label Switching (MPLS) technique that we will discuss in another revision of this book can be considered as a good compromise between datagram and virtual circuits. MPLS uses virtual circuits between routers, but does not extend them to the endhosts. Additional information about MPLS may be found in [ML2011]_.

Tanto la organización de datagramas como la de circuitos virtuales tienen ventajas y desventajas. La principal ventaja de la organización de datagramas es que los hosts pueden enviar fácilmente paquetes a cualquier número de destinos, mientras que la organización de circuitos virtuales requiere el establecimiento de un circuito virtual antes de la transmisión de un paquete de datos. Esta solución puede ser costosa para hosts que intercambian cantidades pequeñas de datos. Por otro lado, la principal ventaja de la organización de circuitos virtuales es que el algoritmo de reenvío usado por los routers es más simple que al usar la organización de datagramas. La utilización de circuitos virtuales puede lograr que la carga esté mejor distribuida sobre la red, gracias a la utilización de múltiples circuitos virtuales. La técnica de conmutación por rótulos multiprotocolo (`MultiProtocol Label Switching`, MPLS) que discutiremos en otra revisión de este libro puede ser considerada un buen compromiso entre datagramas y circuitos virtuales. MPLS usa circuitos virtuales entre routers, pero no los extiende a los sistemas finales. Más información sobre MPLS en [ML2011]_.

.. maybe add more information

.. The control plane
El plano de control
===================

.. One of the objectives of the `control plane` in the network layer is to maintain the routing tables that are used on all routers. As indicated earlier, a routing table is a data structure that contains, for each destination address (or block of addresses) known by the router, the outgoing interface over which the router must forward a packet destined to this address. The routing table may also contain additional information such as the address of the next router on the path towards the destination or an estimation of the cost of this path. 

.. In this section, we discuss the three main techniques that can be used to maintain the routing tables in a network.

Uno de los objetivos del `plano de control` en la capa de Red es mantener las tablas de ruteo que se usan en todos los routers. Como se indicó anteriormente, una tabla de ruteo es una estructura de datos que contiene, para cada dirección destino (o bloque de direcciones) conocida por el router, la interfaz de salida por la cual el router debe reenviar un paquete destinado a dicha dirección. La tabla de ruteo puede también contener información adicional tal como la dirección del siguiente router en el camino hacia el destino, o una estimación del costo de este camino.

En esta sección, discutiremos las tres técnicas principales que pueden usarse para mantener las tablas de ruteo en una red.


.. Static routing
Ruteo estático
--------------

.. comment:: comment formaliser l'absence de boucles

.. The simplest solution is to pre-compute all the routing tables of all routers and to install them on each router. Several algorithms can be used to compute these tables. 

La solución más simple es pre-computar todas las tablas de ruteo de todos los routers e instalarlas en cada uno. Para computar estas tablas pueden usarse varios algoritmos. 

.. A simple solution is to use shortest path routing and to minimise the number of intermediate routers to reach each destination. More complex algorithms can take into account the expected load on the links to ensure that congestion does not occur for a given traffic demand. These algorithms must all ensure that :

.. - all routers are configured with a route to reach each destination
.. - none of the paths composed with the entries found in the routing tables contain a cycle. Such a cycle would lead to a forwarding loop.

Una solución sencilla es usar el ruteo de camino más corto y minimizar la cantidad de routers intermedios para alcanzar cada destino. Algunos algoritmos más complejos pueden tomar en cuenta la carga esperada sobre los enlaces, para asegurar que no ocurra congestión para una demanda de tráfico dada. Todos estos algoritmos deben asegurar que:

 - Todos los routers queden configurados con una ruta hacia cada destino.
 - Ninguno de los caminos conformados por los elementos encontrados en las tablas de ruteo contenga un ciclo. Esos ciclos llevarían a un ciclo de reenvío.

.. The figure below shows sample routing tables in a five routers network.
La figura siguiente ejemplifica las tablas de ruteo en una red de cinco routers.


.. figure:: svg/routing-tables.png
   :align: center
   :scale: 70   

   Tablas de ruteo en una red sencilla
..   Routing tables in a simple network 

.. The main drawback of static routing is that it does not adapt to the evolution of the network. When a new router or link is added, all routing tables must be recomputed. Furthermore, when a link or router fails, the routing tables must be updated as well.

La principal desventaja del ruteo estático es que no se adapta a la evolución de la red. Cuando se agrega un nuevo router o enlace, todas las tablas de ruteo deben ser recalculadas. Además, las tablas de ruteo también deben ser actualizadas cuando falla un enlace o un router.

.. include:: dv.rst

..  include:: linkstate.rst
