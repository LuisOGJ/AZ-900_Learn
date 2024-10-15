Ventajas de los servicios en la nube
==  

**Objetivos:**
- Describir las ventajas de la alta disponibilidad y escalabilidad en la nube.
- Describir las ventajas de la confiabilidad y la previsibilidad en la nube.
- Describir las ventajas de la seguridad y la gobernanza en la nube.
- Describir las ventajas de la capacidad de administración en la nube.  

\
**Alta Disponibilidad**  
La alta disponibilidad se centra en garantizar la ``máxima disponibilidad``, independientemente de las interrupciones o eventos que puedan producirse. deberá tener en cuenta las garantías de disponibilidad del servicio. ``Azure es un entorno de nube de alta disponibilidad con garantías de tiempo de actividad`` en función del servicio. Estas garantías forman parte de los ``contratos de nivel de servicio``.  

\
**Escalabilidad**  
La escalabilidad hace referencia a la ``capacidad de ajustar los recursos para satisfacer la demanda``. Si de pronto experimenta un tráfico máximo y los sistemas están sobrecargados, la capacidad de ``escalar implica que puede agregar más recursos`` para controlar mejor la mayor demanda.  
- Escalado vertical: 
    - Si estuviera desarrollando una aplicación y necesitase más potencia de procesamiento, podría ``escalar verticalmente para agregar más CPU o RAM`` a la máquina virtual. Por el contrario, si se diese cuenta de que ha sobre especificado las necesidades, ``podría reducir verticalmente disminuyendo las especificaciones de CPU o RAM``.
- Escalado horizontal: 
    - si de repente experimentase un salto elevado en la demanda, los recursos implementados se podrían escalar horizontalmente (ya sea de forma automática o manual). Por ejemplo, ``podría agregar máquinas virtuales o contenedores adicionales, mediante el escalado horizontal``. De la misma manera, si hubiera una caída significativa en la demanda, los recursos implementados se podrían escalar (ya sea de forma automática o manual), mediante el escalado horizontal.

\
**Confiabilidad**  
La confiabilidad es la ``capacidad de un sistema de recuperarse de los errores y seguir funcionando``. La nube, debido a su ``diseño descentralizado``, admite de forma natural una ``infraestructura confiable y resistente``. Con un diseño descentralizado, la nube le permite implementar ``recursos en regiones de todo el mundo``. Con esta escala global, incluso si se produce una catástrofe en una región, otras siguen en funcionamiento. ``En algunos casos, el propio entorno en la nube cambiará automáticamente a otra región, sin que tenga que realizar ninguna acción``.  

\
**Predicción**  
La previsibilidad ``se puede centrar en el rendimiento o los costos``. Tanto la previsibilidad de rendimiento como la de costos están muy influidas por el Marco de arquitectura de Microsoft Azure. Implemente una solución creada en torno a este marco, que sea ``predecible en relación con el coste y el rendimiento``.  

\
**Rendimiento**  
La previsibilidad del ``rendimiento se centra en predecir los recursos necesarios para ofrecer una experiencia positiva para los clientes``. El escalado automático, el equilibrio de carga y la alta disponibilidad son solo algunos de los conceptos de nube que admiten la previsibilidad del rendimiento. Si el tráfico se concentra principalmente en un área, ``el equilibrio de carga ayudará a redirigir parte de la sobrecarga a áreas con menos estrés``.  

\
**Coste**  
La predicción de costos ``se centra en pronosticar el costo del gasto en la nube``. Con la nube, puede realizar el seguimiento del uso de recursos en tiempo real, ``supervisar los recursos para asegurarse de que los usa de la manera más eficaz`` y aplicar análisis de datos para buscar patrones y tendencias que ayuden a planear mejor las implementaciones de recursos.  

\
**seguridad y la gobernanza**  
Tanto si va a implementar infraestructura como servicio o software como servicio, ``las características en la nube admiten el cumplimiento y la gobernanza. Aspectos como las plantillas de conjunto ayudan a garantizar que todos los recursos implementados cumplan los estándares corporativos y los requisitos normativos de gobierno``.  
Del lado de la seguridad, puede encontrar una solución en la nube que coincida con sus necesidades de seguridad. Si quiere tener un ``control máximo de la seguridad, la infraestructura como servicio le proporciona recursos físicos, pero le permite administrar los sistemas operativos y el software instalado, incluidas las revisiones y el mantenimiento``. Si quiere que las revisiones y el mantenimiento se administren automáticamente, las implementaciones de plataforma como servicio o software como servicio pueden ser las mejores estrategias en la nube.  
los proveedores de nube suelen ser adecuados para controlar cosas como ataques de denegación de servicio distribuido (DDoS), lo que hace que la red sea más sólida y segura.  

\
**Administración de la nube**  
- Mediante un portal web.
- Con una interfaz de línea de comandos básica.
- Mediante las API.
- Mediante PowerShell.