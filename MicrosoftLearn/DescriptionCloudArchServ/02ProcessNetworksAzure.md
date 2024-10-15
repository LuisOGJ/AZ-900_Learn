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
App Service permite ``crear y hospedar aplicaciones web``, trabajos en segundo plano, back-ends móviles y API RESTful en el lenguaje de programación que prefiera, ``sin tener que administrar la infraestructura``.  