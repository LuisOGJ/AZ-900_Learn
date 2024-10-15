Módulo 02  
==  

- **1. Componentes de la arquitectura de Azure**
    - Regiones y zonas de disponibilidad
    - Suscripciones y grupos de recursos
- **2. Procesos y redes**
    - Tipos de proceso
    - Hospedaje de aplicaciones
    - Redes virtuales
- **3. Almacenamiento**
    - Servicios de almacenamiento
    - Opciones de redundancia
    - Administración y migración de archivos
- **4. Identidad, acceso y seguridad**
    - Servicios de directorio
    - Métodos de autenticación
    - Modelos de seguridad

\
Preguntas
==
- ¿Ques es Microsoft Azure operado por 21Vianet?
    - R: Instancia seperada fisicamente de la nube ubicada en China - Shangai

- ¿Se puede conetar las regiones gloabas de Azure con Azure China?
    - R: Están fisicamente desconectadas, sin embargo puede conectarse vía VPN

- Diferencia entre Azure Virtual Desktop y Windows 365.
    - R: AVD cuento con un modelo de pago por uso, mientras que Windows 365 es un modelo basado en el licenciamiento.  

- Que tipo de categoría o servicio tienen los contenedores
    - R: PaaS

- La opción más fácil, escalable, con alta disponibilidad sin preocupación por el sistema operativo para webs.
    - R: App Services

- Cual es el tipo de storage en Azure que permite tener una sincronización de archivos entre sitios locales y máquinas virtuales en azure.
    - R: Azure Files

- Cual es el objetivo principal de la defensa en produndidad.
    - R: Realentizar el avance del ataque dirigido a adquirir el acceso a los datos.  

\
Simulador - Modulo 2
==  
- ¿Qué herramienta mantiene automáticamente los archivos entre un servidor Windows local y un entorno de nube de Azure actualizado?
    - Azure File Sync  

- ¿Cuál es el número máximo de subscripciones de Azure puede tener asociadas una cuenta de Azure?
    - No hay un límite de subscripciones

- ¿En cuántos grupos de recursos puede estar un recurso al mismo tiempo?
    - Uno

- ¿Qué ocurre con los recursos de un grupo de recursos cuando se aplica una acción o configuración en el nivel de grupo de recursos?
    - La configuración se aplica a los recursos actuales y futuros.

- El **Inicio de sesión único (SSO Single Sign On)** es un método __________ que permite a los usuarios iniciar sesión por primera vez y acceder a varias aplicaciones y recursos utilizando la misma contraseña.
    - Autenticación

- Su empresa tiene centros de datos en Los Ángeles y Nueva York. La empresa tiene una suscripción de Microsoft Azure. Está configurando los dos centros de datos como sitios agrupados geográficamente para la resistencia del sitio. Debe recomendar una opción de redundancia de almacenamiento de Azure. Tiene los siguientes requisitos de almacenamiento de datos: 1. Los datos deben almacenarse en varios nodos. 2. Los datos deben almacenarse en nodos en ubicaciones geográficas separadas. 3. Los datos se pueden leer tanto desde la ubicación secundaria como desde la ubicación principal. ¿Cuál de las siguientes opciones de redundancia almacenada en Azure debería recomendar?  
    - Redundancia geográfica con acceso de lectura (RA-GRS)

- ¿De qué componentes están formados los conjuntos de disponibilidad?
    - Dominios de actualización y Dominios de error

- ¿Qué estrategia emplea una serie de mecanismos para frenar el avance de un ataque destinado a lograr un acceso no autorizado a los datos?
    - Defensa a profundidad

- ¿Qué es el Acceso Condicional en Microsoft Entra ID (Antes conocido como Azure AD) y cuál es su propósito principal?
    - Es una característica que permite a los administrador implementar políticas de seguridad basadas en condiciones específicas para controlar el acceso a las aplicaciones en la nube.

