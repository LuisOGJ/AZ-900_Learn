**Almacenamiento en Azure**
==  
Obtendrá información sobre la cuenta de Azure Storage y cómo se relaciona con ``los distintos servicios de almacenamiento que hay disponibles``. También descubrirá los ``niveles de almacenamiento de blobs``, las ``opciones de redundancia de datos`` y las ``formas de mover datos o incluso infraestructuras completas a Azure``.  

**Objetivos**
- Comparación de los servicios de almacenamiento de Azure.
- Describir los niveles de almacenamiento.
- Describir las opciones de redundancia.
- Describir las opciones de la cuenta de almacenamiento y los tipos de almacenamiento
- Identificar opciones para mover archivos, incluidos AzCopy, Explorador de Azure Storage y Azure File Sync.
- Descripción de las opciones de migración, incluidas Azure Migrate y Azure Data Box.

\
**Cuentas de almacenamiento de Azure**
==  
Proporciona un ``espacio de nombres único`` para los datos de Azure Storage al que se puede ``acceder desde cualquier lugar del mundo a través de HTTP o HTTPS``. Los datos de esta cuenta son seguros, de alta disponibilidad, duraderos y escalables de forma masiva.  
Al crear la cuenta de almacenamiento, ``primero seleccionará el tipo de cuenta de almacenamiento``. El ``tipo de cuenta determina los servicios de almacenamiento y las opciones de redundancia, y afecta a los casos de uso``. A continuación se muestra una ``lista de opciones de redundancia`` que se describirán más adelante en este módulo:
- Almacenamiento con redundancia local (LRS)
- Almacenamiento con redundancia geográfica (GRS)
- Almacenamiento con redundancia geográfica con acceso de lectura (RA-GRS)
- Almacenamiento con redundancia de zona (ZRS)
- Almacenamiento con redundancia de zona geográfica (GZRS)
- Almacenamiento con redundancia de zona geográfica con acceso de lectura (RA-GZRS)  

|Tipo|Servicios Adminitidos|Operaciones de redundancia|Uso|
|-|-|-|-|
|De uso general estándar, V2|Blob Storage (incluido Data Lake Storage), Queue Storage, Table Storage y Azure Files|LRS, GRS, RA-GRS, ZRS, GZRS, RA-GZRS|Tipo de cuenta de almacenamiento estándar para blobs, archivos, colas y tablas. Se recomienda para la mayoría de los escenarios con ``Azure Storage``. Si desea ``compatibilidad con el sistema de archivos de red (NFS) en Azure Files``, utilice el tipo de cuenta de recursos compartidos de archivos Premium|
|Blobs en bloques Premium|Blob Storage (incluido Data Lake Storage)|LRS, ZRS|Tipo de cuenta de almacenamiento Prémium para blobs en bloques y blobs en anexos. ``Se recomiendan para escenarios con altas tasas de transacciones``, que utilizan objetos más pequeños o que ``requieren una latencia de almacenamiento constantemente baja``.|
|Recursos compartidos de archivos|Azure Files|LRS, ZRS|Tipo de cuenta de almacenamiento Prémium solo para recursos compartidos de archivos. Se recomienda para ``empresas y aplicaciones de escalado de alto rendimiento``. Use este tipo de cuenta si desea una cuenta de almacenamiento que admita recursos compartidos de archivos de Bloque de mensajes del servidor (SMB) y NFS.|
|Blobs en páginas Premium|Solo blobs en páginas|LRS|Tipo de cuenta de almacenamiento prémium solo para blobs en páginas.|  

\
**Puntos de conexión de cuenta de almacenamiento**  
Una de las ventajas de usar una cuenta de Azure Storage es ``tener un espacio de nombres único en Azure para los datos``. La combinación del ``nombre de la cuenta y el punto de conexión del servicio de Azure Storage forma los puntos de conexión de su cuenta de almacenamiento``.  
- Los nombres de las cuentas de almacenamiento deben tener ``entre 3 y 24 caracteres``, y solo pueden incluir números y letras en minúscula.
- El nombre de la cuenta de almacenamiento debe ser ``único dentro de Azure``. No puede haber dos cuentas de almacenamiento con el mismo nombre. Esto admite la capacidad de tener un espacio de nombres único y accesible en Azure.  

|Servicio de Storage|Punto de conexión|
|-|-|
|Blob Storage|https://[storage-account-name].blob.core.windows.net|
|Data Leak Storage Gen2|https://[storage-account-name].dfs.core.windows.net|
|Azure Files|https://[storage-account-name].file.core.windows.net|
|Queue Storage|https://[storage-account-name].queue.core.windows.net|
|Table Storage|https://[storage-account-name].table.core.windows.net|

\
**Redundancia de almacenamiento de Azure**
==  
Azure Storage siempre almacena varias copias de los datos. La redundancia garantiza que la cuenta de almacenamiento cumple sus objetivos de disponibilidad y durabilidad, aunque se produzcan errores. Entre los factores que ayudan a determinar qué opción de redundancia debe elegir se incluye:  
- ``Cómo se replican`` los datos en la ``región primaria``.
- Si los datos se ``replican en una segunda ubicación`` que está ``alejada geográficamente`` de la región primaria, para protegerse frente a desastres regionales.
- Si la ``aplicación necesita acceso de lectura`` a los datos replicados en la región secundaria en caso de que la región primaria deje de estar disponible.  

\
**Redundancia en la región primaria**  
Los datos de una cuenta de Azure Storage siempre se ``replican tres veces en la región primaria``. Azure Storage ofrece ``dos opciones para replicar los datos`` en la región primaria, el almacenamiento con ``redundancia local (LRS)`` y el almacenamiento con ``redundancia de zona (ZRS)``.  

**Almacenamiento con redundancia local**  
