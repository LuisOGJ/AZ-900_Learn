Principales componentes arquitectónicos de Azure
==  
``organización física`` de Azure: ``centros de datos, zonas de disponibilidad y regiones``; y también sobre la ``estructura organizativa`` de Azure: ``recursos y grupos de recursos, suscripciones y grupos de administración``.  

**Objetivos**  
- Describir las regiones de Azure, los pares de regiones y las regiones soberanas.
- Describir las zonas de disponibilidad.
- Describir los centros de datos de Azure.
- Describir los recursos y grupos de recursos de Azure.
- Describir las suscripciones.
- Describir los grupos de administración.
- Describir la jerarquía de grupos de recursos, suscripciones y grupos de administración.  

**Azure**  
Azure es un conjunto de ``servicios en la nube``. Azure le ofrece la libertad de ``compilar, administrar e implementar aplicaciones`` en una red global masiva mediante sus ``herramientas y plataformas`` favoritas.  
- Ofrece: 
    - Innovación ilimitada
    - Haga realidad las ideas
    - Unifique sin problemas
    - Innove en la confianza
- Puede hacer con Azure: 
    - Muchos equipos comienzan a explorar la nube mediante la ``migración de sus aplicaciones existentes a máquinas virtuales (VM) que se ejecutan en Azure``. Aunque este es un buen comienzo, la nube es mucho más que un lugar diferente donde ejecutar las máquinas virtuales.

\
**Cuentas de Azure**  
==  
Después de crear una cuenta de Azure, puedes ``crear suscripciones adicionales``. Por ejemplo, es posible que la empresa use una única cuenta de Azure para el negocio y ``suscripciones independientes para los departamentos de desarrollo, marketing y ventas``. Una vez que has creado una suscripción de Azure, puedes empezar a crear recursos de Azure dentro de cada suscripción.  

![](/Mod2/images/7.png)  

\
**Infraestructura física de azure**  
==  
A lo largo del recorrido con Microsoft Azure, escucharás y usarás términos como ``regiones, zonas de disponibilidad, recursos, suscripciones``, etc. Este módulo se centra en los principales componentes arquitectónicos de Azure. Los ``componentes arquitectónicos principales de Azure se pueden dividir en dos grandes grupos: la infraestructura física y la infraestructura de administración``.  

**Infraestructura física**  
La ``infraestructura física de Azure comienza con los centros de datos``. Azure tiene ``centros de datos en todo el mundo``. Pero estos centros de datos individuales no son accesibles directamente. ``Los centros de datos se agrupan en regiones de Azure`` o ``Azure Availability Zones``, están diseñados para ayudarte a lograr resistencia y confiabilidad para las cargas de trabajo críticas para la empresa.  

**Regions**  
Una región es un`` área geográfica del planeta que contiene al menos un centro de datos``, aunque podrían ser varios cercanos y conectados mediante una red de baja latencia. Azure asigna y controla los recursos de forma inteligente dentro de cada región para garantizar que las cargas de trabajo están bien compensadas.  

**Availability Zones**  
Las zonas de disponibilidad son ``centros de datos separados físicamente dentro de una región de Azure``. Cada zona de disponibilidad ``consta de uno o varios centros de datos equipados con alimentación, refrigeración y redes independientes``. Una zona de disponibilidad se ``configura para constituir un límite de aislamiento``. Si ``una zona deja de funcionar, la otra continúa trabajando``. Las zonas de disponibilidad están ``conectadas`` a través de redes de ``fibra óptica de alta velocidad privadas``.  

![](/Mod2/images/2.png)  

**Regiones Soberanas**
- ``US DoD (centro), US Gov Virginia, US Gov Iowa y más``: Estas regiones son instancias físicas y lógicas con aislamiento de red de Azure para asociados y agencias de la administración pública de EE. UU. Estos centros de datos están operados por personal estadounidense sometido a evaluación e incluyen certificaciones de cumplimiento adicionales.
- ``Este de China, Norte de China y más``: Estas regiones están disponibles gracias a una asociación exclusiva entre Microsoft y 21Vianet, por la cual Microsoft no mantiene directamente los centros de datos.  

\
**Infraestructura de Administración de Azure**  
==  
 Incluye ``recursos de Azure y grupos de recursos, suscripciones y cuentas``. Comprender la organización jerárquica le ayudará a planear los proyectos y productos dentro de Azure.  

 **Recurss y grupos de recursos de Azure**  
 Un recurso es el bloque de creación básico de Azure. Todo lo que cree, aprovisione, implemente, etc., es un recurso.  

 ![](/Mod2/images/5.png)

 Los grupos de recursos ``proporcionan una manera cómoda de agrupar recursos``. Al aplicar una ``acción a un grupo de recursos, se aplicará a todos los recursos`` que contiene. Si elimina un grupo de recursos, se eliminarán todos los recursos que contiene.

 **Suscripciones de Azure**  
 las suscripciones son una ``unidad de administración, facturación y escala``. Al igual que los grupos de recursos son una manera de organizar lógicamente los recursos, las suscripciones ``permiten organizar lógicamente los grupos de recursos y facilitar la facturación``.  

  ![](/Mod2/images/6.png)

``Una suscripción le proporciona acceso autenticado y autorizado a los servicios y productos de Azure``. Una suscripción de Azure se vincula a una cuenta de Azure, que es una identidad de Microsoft Entra ID o en un directorio en el que confía Microsoft Entra ID.  
``Una cuenta puede tener varias suscripciones``, pero solo es obligatorio tener una. En una cuenta de varias suscripciones, puede usarlas para configurar diferentes modelos de facturación y aplicar diferentes directivas de administración de acceso.  
- Límite de facturación
- Límite de control de acceso

**Creación de una suscripción de Azure adicional**  
Puedes optar por crear suscripciones adicionales para separar lo siguiente:  
- Entornos
- Estructuras organizativas
- Facturación  

**Grupos de administración de Azure**  
La última pieza es el grupo de administración. ``Los recursos se recopilan en grupos de recursos y los grupos de recursos se recopilan en suscripciones``. Si acaba de empezar en Azure, podría parecer una jerarquía suficiente para mantener las cosas organizadas. Pero imagine que trabaja con varias aplicaciones, varios equipos de desarrollo, en varias zonas geográficas.  
Los grupos de administración de Azure ``proporcionan un nivel de ámbito por encima de las suscripciones``. Las suscripciones ``se organizan en contenedores llamados grupos de administración``, a los que se ``aplican condiciones de gobernanza``.  

**Jerarquía de grupo de administración, suscripciones y grupo de recursos**  

![](/MicrosoftLearn/images/01.png)

Ejemplos de cómo podría usar los grupos de administración podrían ser los siguientes:
- Crear una jerarquía que aplique una directiva
- Proporcionar acceso de usuario a varias suscripciones  

Importante:
- Se ``admiten 10 000 grupos`` de administración en un único directorio.
- Un árbol de grupo de administración puede admitir ``hasta seis niveles de profundidad``.
- Cada grupo de administración y suscripción ``solo puede admitir un elemento primario``.