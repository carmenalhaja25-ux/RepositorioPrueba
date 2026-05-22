

# 

# 

# 

# El Marco Legal y la Estructura del "Relato"

**Carmen Alhaja García**  
**15/05/2016**  
**Sistemas Informáticos**

# ÍNDICE

[1\. Análisis de Necesidades	3](#1.-análisis-de-necesidades)

[1.1. Contexto y Problemática Actual	3](#1.1.-contexto-y-problemática-actual)

[1.2. Solución Propuesta: Infraestructura Híbrida Docker-Guacamole	3](#1.2.-solución-propuesta:-infraestructura-híbrida-docker-guacamole)

[1.3. Justificación Técnica y Beneficios (TCO)	3](#1.3.-justificación-técnica-y-beneficios-\(tco\))

# ANEXO I: Plantilla y Ejemplo de Análisis de Necesidades

# 1\. Análisis de Necesidades {#1.-análisis-de-necesidades}

## 1.1. Contexto y Problemática Actual {#1.1.-contexto-y-problemática-actual}

**\[Instrucción: Explica en qué situación se encuentra la empresa antes de tu intervención\]**

La empresa objeto de este proyecto, una startup de desarrollo multiplataforma, requería que sus técnicos accedieran a servidores de bases de datos y desarrollo ubicados en un centro de datos remoto. La situación inicial presentaba riesgos de seguridad críticos, ya que se dependía de la apertura de múltiples puertos en el firewall para protocolos RDP y SSH directos, lo que aumentaba la superficie de ataque del sistema.

## 1.2. Solución Propuesta: Infraestructura Híbrida Docker-Guacamole {#1.2.-solución-propuesta:-infraestructura-híbrida-docker-guacamole}

**\[Instrucción: Describe qué has montado y por qué esa tecnología exacta\]** 

Tras analizar los requerimientos de accesibilidad y seguridad (RA6), se ha optado por implementar una solución basada en **Apache Guacamole** desplegada mediante **Docker Compose**. Esta arquitectura permite:

* **Centralización**. Un único punto de acceso vía web (puerto 8080/443) para todos los servicios internos.  
* **Aislamiento**. Gracias a los contenedores, cada servicio (PostgreSQL, Guacamole, SSH) opera en su propio entorno estanco, evitando conflictos de dependencias.  
* **Seguridad**. Se elimina la necesidad de clientes externos pesados, permitiendo una auditoría centralizada de las conexiones.

## 1.3. Justificación Técnica y Beneficios (TCO) {#1.3.-justificación-técnica-y-beneficios-(tco)}

**\[Instrucción: Convence al lector de que tu solución es rentable y profesional\]**

La elección de esta solución responde a la necesidad de optimizar el **Coste Total de Propiedad (TCO)**. Al utilizar software bajo licencias permisivas (Apache y PostgreSQL License), la empresa evita costes de licenciamiento recurrentes, pudiendo reinvertir ese capital en la seguridad de la infraestructura.

Además, la portabilidad que ofrece Docker garantiza que el tiempo de recuperación ante desastres (DRP) sea mínimo, cumpliendo con los requisitos no funcionales de disponibilidad que todo sistema informático profesional debe garantizar.

**Consejos para tu redacción**:

1. **Habla en tercera persona**. Evita el "yo he puesto" o "nosotros hemos hecho". Usa "se ha implementado", "se observa", "la solución permite".  
2. **Usa conectores**. Palabras como "*por consiguiente*", "*en consecuencia*", "*asimismo*" o "*no obstante*" le dan a tu texto un aire de ingeniero que te va a venir muy bien en el futuro.  
3. **Cita siempre (IEEE)**. Si dices que el software libre es mejor, di quién lo apoya o en qué norma se basa.

**Buenos ejemplos**:
* Drake, J. M. (2008). **Análisis de requisitos y especificación de una aplicación** \[en línea\] Disponible en: https://www.ctr.unican.es/asignaturas/ingenieria\_software\_4\_f/doc/m3\_08\_especificacion-2011.pdf  
* García Notario, D. (2015). **Análisis de requisitos en el desarrollo del software**  \[en línea\] Disponible en: https://e-archivo.uc3m.es/rest/api/core/bitstreams/a66b0a2d-fa7c-483f-ac5e-1476ff2da8eb/content

# 2. Estimación de Costes de Infraestructura

<img width="1342" height="382" alt="Captura de pantalla 2026-05-22 095935" src="https://github.com/user-attachments/assets/11b51666-a5f6-4099-b3fb-6b2770e4c388" />

# 3. Estrategia de Despliegue y Comunicación

Para trasladar la aplicación desde el Entorno de Desarrollo local hacia el servidor de producción, se implementará un flujo de despliegue automatizado basado en SFTP. Descartamos la opción de FTP tradicional porque es mas vulnerable al transmitir ciertos archivos y datos en texto plano. SFTP opera sobre el puerto seguro estándar 22, garantizando el cifrado de extremo a extremo y la autenticación mediante claves criptográficas SSH robustas, lo que blinda la infraestructura ante ataques de intercepción de tráfico.

En cuanto a la comunicación del equipo y la gestión de incidencias operativas, se integrará un sistema de alertas automatizadas en un canal privado de Discord. Ante cualquier anomalia crítica como una caída del servidor o saturación de memoria, un script en producción enviará notificaciones instantáneas detallando el código de error y el estado del sistema, permitiendo una monitorización reactiva y una intervención inmediata frente a ellos. 

# 4. Justificación Científica

