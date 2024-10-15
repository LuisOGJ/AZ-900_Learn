Servicios de proceso y redes de Azure
==  
Obtendrá información sobre tres de las ``opciones de proceso`` (``máquinas virtuales, contenedores y funciones de Azure``). También obtendrá información sobre algunas de las características de ``red, como las redes virtuales de Azure, Azure DNS y Azure ExpressRoute``.  

**Objetivos**  
- ``Comparar`` los tipos de ``proceso``, incluidas las instancias de ``contenedor``, las ``máquinas virtuales`` y las ``funciones``.
- Describir las ``opciones de máquina virtual``, incluidas las ``máquinas virtuales (VM)``, los ``conjuntos de escalado`` de máquinas virtuales, los ``conjuntos de disponibilidad`` de máquinas virtuales y ``Azure Virtual Desktop``.  
- Describir los ``recursos necesarios`` para las máquinas virtuales.
- Describir las opciones de ``hospedaje de aplicaciones``, incluidos ``Azure Web Apps``, ``contenedores`` y ``máquinas virtuales``.
- Describir las ``redes virtuales``, incluido el propósito de ``Azure Virtual Networks``, las ``subredes virtuales`` de Azure, el ``emparejamiento``, ``Azure DNS``, ``VPN Gateway`` y ``ExpressRoute``.
- Definir ``puntos de conexión públicos y privados``.  

\
**Azure Virtual Machines (VM)**  
==  
Estas máquinas virtuales proporcionan una ``infraestructura como servicio (IaaS)`` en forma de un ``servidor virtualizado`` y se pueden usar de muchas formas. Como sucede en un equipo físico, puedes ``personalizar todo el software que se ejecuta en la máquina virtual``.
- ``Control`` total sobre el sistema operativo(SO).
- Capacidad de ``ejecutar software personalizado``.
- Usar ``configuraciones de hospedaje personalizadas``.  

Te ofrece la ``flexibilidad de la virtualización`` sin necesidad de adquirir y mantener el hardware físico que ejecuta la máquina virtual. Pero, como oferta de IaaS, ``tendrá que configurar, actualizar y mantener el software`` que se ejecuta en la máquina virtual.  

**Escalado de máquinas virtuales en Azure**  
Se pueden agrupar las máquinas virtuales para ``proporcionar alta disponibilidad, escalabilidad y redundancia``. Azure también puede ``administrar la agrupación de máquinas`` virtuales con características como ``conjuntos de escalado y conjuntos de disponibilidad``.  

**Conjuntos de escalado de máquinas virtuales**  
Permiten ``crear y administrar un grupo de máquinas virtuales idénticas, de carga equilibrada``. Los conjuntos de escalado le ``permiten administrar, configurar y actualizar de forma centralizada`` un gran número de máquinas virtuales ``en cuestión de minutos``. ``El número de instancias de máquina virtual puede aumentar o disminuir automáticamente según la demanda``, o bien puede establecerlo para que se ``escale en función de una programación definida``. ``Implementan automáticamente un equilibrador de carga`` para asegurarse de que los recursos se usan de forma eficaz.  

**Conjuntos de disponibilidad de máquinas virtuales**  
Los conjuntos de disponibilidad de máquinas virtuales son otra herramienta que le ayudará a ``crear un entorno más resistente y de alta disponibilidad``. Diseñados para ``garantizar`` que las máquinas virtuales escalen las ``actualizaciones y tengan una conectividad de red y potencia variadas``, lo que evita que se pierdan todas las máquinas virtuales debido a un solo fallo de energía o de la red. La disponibilidad logra estos objetivos mediante ``la agrupación de máquinas virtuales de dos maneras``: actualizar el dominio y el dominio de error.
- *Dominio de actualización:* ``agrupa las máquinas virtuales que se pueden reiniciar al mismo tiempo``. Permite aplicar actualizaciones al saber que solo una agrupación de dominios de actualización está sin conexión a la vez. 
- *Dominio de error:* ``agrupa las máquinas virtuales por fuente de alimentación común y conmutador de red``. Un conjunto de disponibilidad divide las máquinas virtuales en hasta tres dominios de error.  

**Ejemplos de uso**
- Durante las pruebas y el desarrollo
- Al ejecutar aplicaciones en la nube
- Al ampliar el centro de datos a la nube
- Durante la recuperación ante desastres
- Lift-and-shift

**Recursos de máquina virtual**  
- Tamaño (propósito, número de núcleos de procesador y cantidad de RAM)
- Discos de almacenamiento (unidades de disco duro, unidades de estado sólido, etc.)
- Redes (red virtual, dirección IP pública y configuración de puertos)  

**Creación de una máquina virtual Linux e instalación de Nginx**
- Creación de la máquina virtual
```
az vm create \
  --resource-group "learn-01c0c4b5-b718-4711-ab21-eabdc6020337" \
  --name my-vm \
  --public-ip-sku Standard \
  --image Ubuntu2204 \
  --admin-username azureuser \
  --generate-ssh-keys  
```
- Cnfiguración de Nginx
```
az vm extension set \
  --resource-group "learn-01c0c4b5-b718-4711-ab21-eabdc6020337" \
  --vm-name my-vm \
  --name customScript \
  --publisher Microsoft.Azure.Extensions \
  --version 2.1 \
  --settings '{"fileUris":["https://raw.githubusercontent.com/MicrosoftDocs/mslearn-welcome-to-azure/master/configure-nginx.sh"]}' \
  --protected-settings '{"commandToExecute": "./configure-nginx.sh"}'   
```  

\
**Azure Virtual Desktop**
==  
Azure Virtual Desktop es un ``servicio de virtualización de escritorios y aplicaciones`` que se ejecuta en la nube. Usar una versión hospedada en la nube de Windows ``desde cualquier ubicación``. Puede usar para acceder a escritorios remotos o a la mayoría de exploradores modernos.  

**Aumento de la seguridad**  
Proporciona ``administración centralizada de seguridad`` para los escritorios de los usuarios con Microsoft Entra ID. Puedes habilitar la ``autenticación multifactor`` para proteger los inicios de sesión de los usuarios. También puedes ``proteger el acceso a los datos mediante la asignación a los usuarios de controles de acceso basados en roles (RBAC)`` detallados.  

\
**Contenedores de Azure**  
==  
Los contenedores son una excelente opción si quiere ``ejecutar varias instancias de una aplicación en un solo equipo`` host. A diferencia de las máquinas virtuales, ``no se administra el sistema operativo de un contenedor``. Las máquinas virtuales son similares a una ``instancia de sistema operativo que se puede conectar y administrar``. Con los contenedores ``puede reiniciar rápidamente en caso de bloqueo o interrupción del hardware``. Uno de los motores de contenedores más populares es Docker. Y Azure es compatible con Docker.  

**Azure Container Instances**  
 Plataforma como servicio (``PaaS``), Ofrece la ``forma más rápida y sencilla de ejecutar un contenedor en Azure`` sin tener que administrar máquinas virtuales o adoptar servicios adicionales.

**Azure Container Apps**  
Le permiten ponerse en marcha de inmediato, ``quitan la pieza de administración de contenedores y son una oferta de PaaS``. Container Apps tienen ventajas adicionales, como la ``capacidad de incorporar el equilibrio de carga y el escalado``. Estas otras funciones le permiten ser ``más elásticas en el diseño``.

**Azure Kubernetes Service**  
Es un servicio de ``orquestación de contenedores``. Un servicio de orquestación ``administra el ciclo de vida de los contenedores``. Al implementar una flota de contenedores, ``AKS puede hacer que la administración de flotas sea más sencilla y eficaz``.  

**Ejemplos de usos**
- Los contenedores se usan normalmente para crear soluciones mediante una ``arquitectura de microservicios``.
- Con los contenedores puede ``escalar el back-end por separado para mejorar el rendimiento``.  

\
**Azure Functions**
==  
Azure Functions es una ``opción de proceso sin servidor controlada por eventos`` que ``no necesita el mantenimiento de máquinas virtuales ni contenedores``. Si compila una aplicación mediante máquinas virtuales o contenedores, esos recursos deben "ejecutarse" para que la aplicación funcione. Con Azure Functions, un evento activa la función, lo que reduce la necesidad de mantener los recursos aprovisionados cuando no hay ningún evento.

**Ventajas de Azure Functions**  
El uso de Azure Functions es idóneo si solo le ``interesa el código que ejecuta el servicio y no la infraestructura o la plataforma subyacente``. Las funciones se usan normalmente cuando se debe realizar un trabajo en respuesta a un evento (a menudo a través de una solicitud REST).  
Azure Functions ejecuta el código cuando se desencadena y desasigna automáticamente los recursos cuando finaliza la función. En este modelo, Azure s``olo le cobra por el tiempo de CPU usado mientras se ejecuta la función``.  

\
**Azure App Service**
==  
App Service permite ``crear y hospedar aplicaciones web``, trabajos en segundo plano, back-ends móviles y API RESTful en el lenguaje de programación que prefiera, ``sin tener que administrar la infraestructura``. Azure App Service ``le permite centrarse en la creación y el mantenimiento de la aplicación``, y ``Azure se centra en mantener el entorno en funcionamiento``. Azure App Service es un servicio ``basado en HTTP para hospedar aplicaciones web``, API de REST y back-ends para dispositivos móviles. Admite varios lenguajes, incluidos .NET, .NET Core, Java, Ruby, Node.js, PHP o Python. También admite entornos de Windows y Linux.  

**Tipos de servicios de aplicaciones**
- Aplicaciones web
- Aplicaciones de API
- Trabajos web
- Aplicaciones móviles

\
**Redes Virtuales**
==  
Las redes virtuales y las subredes virtuales de Azure ``permiten a los recursos de Azure``, como las máquinas virtuales, las aplicaciones web y las bases de datos, ``comunicarse entre sí``, con los usuarios de Internet y con los equipos cliente en el entorno local. Las redes virtuales de Azure proporcionan las importantes funcionalidades de red siguientes:
- Aislamiento y segmentación
- Comunicación con internet
- Comunicación entre recurss de Azure
- Comunicación con los recursos locales
- Enrutamiento del tráfico de red
- Filtrado de red
- Conexión de redes virtuales

\
**Aislamiento y segmentación**  
La red virtual de Azure ``permite crear varias redes virtuales aisladas``. Al configurar una red virtual, se ``define un espacio de direcciones IP privadas con intervalos de direcciones IP públicas o privadas``. El intervalo IP solo existe dentro de la red virtual y no es enrutable en Internet. Para la resolución de nombres, ``puede usar el servicio de resolución de nombres integrado en Azure``. También puede configurar la red virtual para que ``use un servidor DNS interno o externo``.  

**Comunicación con Internet**  
Puede permitir ``conexiones entrantes desde Internet`` mediante la ``asignación de una dirección IP pública a un recurso de Azure`` o ``la colocación del recurso detrás de un equilibrador de carga público``.  

**Comunicación entre recursos de Azure**  
- Las redes virtuales ``no solo pueden conectar máquinas virtuales``, sino ``también otros recursos de Azure``, como ``App Service Environment para Power Apps, Azure Kubernetes Service y conjuntos de escalado`` de máquinas virtuales de Azure.
- Los puntos de conexión de servicio se ``pueden conectar a otros tipos de recursos de Azure, como cuentas de almacenamiento y bases de datos de Azure SQL.`` Este enfoque permite vincular varios recursos de Azure con las redes virtuales para mejorar la seguridad y proporcionar un enrutamiento óptimo entre los recursos.  

**Comunicación con recursos locales**  
Las redes virtuales de Azure ``permiten vincular entre sí los recursos del entorno local y dentro de la suscripción de Azure``. De hecho, puede crear una red que abarque tanto el entorno local como el entorno en la nube.  
- Las conexiones de red privada virtual de punto a sitio se establecen desde un equipo ajeno a la organización a la red corporativa. En este caso, el ``equipo cliente inicia una conexión VPN cifrada para conectarse a la red virtual de Azure``.
- Las redes virtuales privadas de sitio a sitio ``vinculan`` el dispositivo o puerta de enlace de ``VPN local con la puerta de enlace de VPN de Azure en una red virtual``. De hecho, puede parecer que los dispositivos de Azure están en la red local. ``La conexión se cifra y funciona a través de Internet``.
- ``Azure ExpressRoute`` proporciona una ``conectividad privada dedicada a Azure que no se desplaza por Internet``. ExpressRoute es útil para los ``entornos donde se necesita más ancho de banda`` e incluso ``mayores niveles de seguridad``.

**Enrutamiento del tráfico de red**  
De forma predeterminada, Azure ``enruta el tráfico entre las subredes de todas las redes virtuales conectadas, las redes locales e Internet``. También puede controlar el enrutamiento e invalidar esa configuración del siguiente modo:
- Las ``tablas de rutas permiten definir reglas sobre cómo se debe dirigir el tráfico``. Puede crear ``tablas de rutas personalizadas que controlen cómo se enrutan los paquetes`` entre las subredes.
- El Protocolo de puerta de enlace de borde (``BGP``) ``funciona con puertas de enlace de VPN de Azure, Azure Route Server o Azure ExpressRoute`` para propagar las rutas BGP locales a las redes virtuales de Azure.

**Filtrado del tráfico de red**
- Los ``grupos de seguridad de red`` son recursos de Azure que pueden contener varias ``reglas de seguridad de entrada y salida``. Estas reglas se pueden definir para ``permitir o bloquear el tráfico`` en función de factores como el protocolo, el puerto y las direcciones IP de destino y origen.
- Las ``aplicaciones virtuales de red`` son máquinas virtuales especializadas que se pueden comparar con un ``dispositivo de red protegido``. Una aplicación virtual de red ejerce una ``función de red determinada, como ejecutar un firewall o realizar la optimización de la red`` de área extensa (WAN).

**Conexión de redes virtuales**  
``Puede vincular redes virtuales entre sí mediante el emparejamiento de red virtual``. El ``tráfico de red entre redes emparejadas es privado y se desplaza por la red troncal de Microsoft``, y nunca entra en la red pública de Internet. Estas redes virtuales ``pueden estar en regiones independientes``. Esta característica le permite crear una ``red interconectada global a través de Azure``.  

\
**Redes privadas Vortuales (VPN)**
==  
Una red privada virtual (VPN) usa un ``túnel cifrado en otra red``. Normalmente, las VPN se ``implementan para conectar entre sí dos o más redes privadas de confianza`` a través de una red que no es de confianza (normalmente, la red pública de Internet).  

Las instancias de ``Azure VPN Gateway`` se implementan en una subred dedicada de la red virtual y permiten la conectividad siguiente:
- Conectar los ``centros de datos locales a redes virtuales`` a través de una ``conexión de sitio a sitio``.
- Conectar los ``dispositivos individuales a redes virtuales`` a través de una ``conexión de punto a sitio``.
- Conectar las ``redes virtuales a otras redes virtuales`` a través de una ``conexión entre redes``.  

Al configurar una instancia de VPN Gateway, ``debe especificar el tipo de red privada virtual, es decir, basada en directivas o basada en rutas``. La distinción principal entre estos dos tipos`` es cómo determinan qué tráfico necesita cifrado``. En Azure, independientemente del tipo de red privada virtual, ``el método de autenticación que se emplea es una clave compartida previamente``.  
- Las instancias de VPN Gateway basadas en ``directivas especifican de forma estática la dirección IP de los paquetes que se deben cifrar a través de cada túnel``. Este tipo de dispositivo evalúa cada paquete de datos en función de los conjuntos de direcciones IP para elegir el túnel a través del cual se va a enviar el paquete.
- En las puertas de enlace basadas en rutas, los ``túneles IPSec se modelan como una interfaz de red`` o una interfaz de túnel virtual. El enrutamiento IP (ya sean rutas estáticas o protocolos de enrutamiento dinámico) ``decide cuál de estas interfaces de túnel se va a usar al enviar cada paquete``.  

Si necesita alguno de los siguientes tipos de conectividad, ``use una instancia de VPN Gateway basada en rutas``:
- Conexiones entre redes virtuales
- Conexiones de punto a sitio
- Conexiones de varios sitios
- Coexistencia con una puerta de enlace de Azure ExpressRoute

\
**Escenarios de alta disponibilidad**  
- Configuración de activo-en espera: las instancias de ``VPN Gateway se implementan como dos instancias en una configuración de activo-en espera``, incluso si solo ve un recurso de VPN Gateway en Azure.
- Activo/activo: En esta configuración, ``se asigna una IP pública única a cada instancia. Después, se crean túneles independientes desde el dispositivo local a cada dirección IP``.
- Conmutación por error de ExpressRoute: Configurar una instancia de VPN Gateway ``como una ruta segura de conmutación por error para las conexiones ExpressRoute``.
- Puertas de enlace con redundancia de zona: Se pueden implementar puertas de enlace VPN y ExpressRoute en una configuración con redundancia de zona.  

\
**Azure ExpressRoute**
==  
ExpressRoute le ``permite ampliar las redes locales a la nube de Microsoft mediante una conexión privada`` con la ayuda de un proveedor de conectividad. Esta conexión se denomina ``circuito ExpressRoute``. ``Las conexiones de ExpressRoute no pasan por la red pública de Internet``. Esta configuración permite que las conexiones de ExpressRoute ofrezcan más confiabilidad, velocidades más rápidas, latencias coherentes y mayor seguridad que las conexiones típicas a través de Internet.

**Características y ventajas de ExpressRoute**  
- Conectividad con los Servicios en la nube de Microsoft
    - Microsoft Office 365
    - Microsoft Dynamics 365
    - Servicios de proceso de Azure, como Azure Virtual Machines
    - Servicios en la nube de Azure, como Azure Cosmos DB y Azure Storage
- Conectividad global: Supongamos que tiene una ``oficina en Asia y un centro de datos en Europa``, ambos con circuitos ExpressRoute que los conectan a la red de Microsoft. Puede usar ``Global Reach de ExpressRoute para conectar esas dos instalaciones``, lo que les ``permite comunicarse sin transferir datos a través de la red pública de Internet``.
- Enrutamiento dinámico: ``ExpressRoute usa el BGP``. Para ``intercambiar rutas entre las redes locales y los recursos que se ejecutan en Azure``.
- Redundancia integrada: Cada proveedor de conectividad ``usa dispositivos redundantes para garantizar que las conexiones establecidas con Microsoft tengan alta disponibilidad``.

\
**Modelos de conectividad de ExpressRoute**
- Coubicación en un intercambio en la nube: Colocación hace referencia a su centro de datos, oficina u otra ``instalación que se coloca físicamente en un intercambio en la nube, como un ISP``.
- Conexión Ethernet de punto a punto: Hace referencia al uso de una ``conexión punto a punto para conectar la instalación a la nube de Microsoft``.
- Redes universales: Azure ``se integra con la conexión WAN para proporcionarle una conexión, como la que tendría entre el centro de datos y las sucursales``.
- Directamente desde sitios de ExpressRoute: ``Puede conectarse directamente a la red global de Microsoft en una ubicación de emparejamiento distribuida estratégicamente por todo el mundo``. ExpressRoute Direct proporciona conectividad dual de 100 Gbps o 10 Gbps, que es compatible con la conectividad activa/activa a escala.

\
**Concideraciones de Seguridad**
- Los datos no viajan a través de la red pública de Internet.
- Es una conexión privada de la infraestructura local a la infraestructura de Azure.
- Incluso si tiene una conexión ExpressRoute, las consultas de DNS, la comprobación de la lista de revocación de certificados y las solicitudes de Azure Content Delivery Network se siguen enviando a través de la red pública de Internet.  

\
**Azure DNS**
==  
es un servicio de ``hospedaje para dominios DNS`` que ofrece resolución de nombres mediante la infraestructura de Microsoft Azure.  

**Ventajas de Azure DNS**
- Confiabilidad y rendimiento: Los dominios DNS de Azure DNS ``se hospedan en la red global de servidores de nombres DNS de Azure``, y proporcionan resistencia y alta disponibilidad.
- Seguridad:
    - Control de acceso basado en rol de Azure (Azure RBAC) para controlar quién accede a acciones específicas en la organización.
    - Registros de actividad
    - Bloqueo de recursos para bloquear una suscripción
- Facilidad de uso: Puede ``administrar los dominios y registros con Azure Portal``, cmdlets de Azure PowerShell y la CLI de Azure multiplataforma. Las aplicaciones que requieren la administración automática de DNS se pueden integrar con el servicio mediante las API REST y los SDK.
- Redes virtuales personalizables con dominios privados: Azure DNS es compatible con dominios DNS privados.
- Registros de alias: Puede usar un conjunto de registros de alias que haga referencia a un recurso de Azure, como una dirección IP pública de Azure, un perfil de Azure Traffic Manager o un punto de conexión de Azure Content Delivery Network (CDN).