# 📉 HL7, FHIR, ISO 27799 y TOGAF en el Sector Salud

##  Introducción

En el sector salud, la gestión de la información clínica, la seguridad de los datos y la arquitectura empresarial son fundamentales. Para abordar estos desafíos, existen estándares y marcos como HL7 (Health Level Seven), FHIR (Fast Healthcare Interoperability Resources), ISO 27799 y TOGAF (The Open Group Architecture Framework), cada uno con enfoques distintos pero complementarios.

-  **HL7** es un marco de interoperabilidad que facilita el intercambio de datos de salud.
-  **FHIR** es un estándar basado en APIs modernas para la integración de sistemas de salud. -> [FHIR](./docs/FHIR-modulos.md)
-  **ISO 27799** proporciona directrices para la seguridad de la información en el sector sanitario. -> [ISO-27799](./docs/ISO-27799-2016.pdf)
-  **TOGAF** es un marco de arquitectura empresarial que ayuda a estructurar y alinear TI con los objetivos del negocio.

Estos marcos pueden combinarse para mejorar la eficiencia, seguridad, cumplimiento normativo y la alineación estratégica en las organizaciones de salud.

##  Objetivos de HL7, FHIR, ISO 27799 y TOGAF

### HL7

- Facilitar la interoperabilidad entre diferentes sistemas de información en salud.
- Definir estándares de mensajería clínica, documentos y terminologías.
- Proveer un marco común para la gestión de historias clínicas electrónicas (EHR).

### FHIR

- Modernizar la interoperabilidad utilizando RESTful APIs y formatos como JSON y XML.
- Acelerar el intercambio de información clínica entre hospitales, clínicas y aseguradoras.
- Facilitar la integración con aplicaciones móviles y plataformas en la nube.

### ISO 27799

- Establecer prácticas para la seguridad de la información en salud, basadas en ISO 27001.
- Proteger la confidencialidad, integridad y disponibilidad de los datos clínicos.
- Cumplir con normativas como HIPAA, GDPR y la Ley N° 29733 en Perú.

### TOGAF

- Proporcionar un marco estructurado para diseñar, planificar e implementar arquitecturas empresariales.
- Alinear la tecnología con los objetivos estratégicos de las organizaciones de salud.
- Facilitar la gestión del cambio y la interoperabilidad entre diferentes sistemas.

##  Alcance de HL7, FHIR, ISO 27799 y TOGAF

|  Estándar | Alcance |
|-------------|-----------|
| **HL7**     | Definición de formatos y protocolos para el intercambio de datos médicos. |
| **FHIR**    | Interoperabilidad basada en APIs para sistemas de salud modernos. |
| **ISO 27799**| Seguridad y gobernanza de la información en sistemas de salud. |
| **TOGAF**   | Diseño y alineamiento estratégico de la arquitectura empresarial en salud. |

## Beneficios de Implementar HL7, FHIR, ISO 27799 y TOGAF

###  HL7

-  Estandariza la comunicación entre sistemas médicos.
-  Permite la interoperabilidad entre hospitales, laboratorios y aseguradoras.
-  Facilita la integración con EHR y PACS (sistemas de imágenes médicas).

###  FHIR

-  Usa tecnologías modernas como APIs RESTful y formatos legibles como JSON.
-  Compatible con aplicaciones móviles y sistemas en la nube.
-  Facilita la integración con IA y analítica de datos en salud.

###  ISO 27799

-  Refuerza la ciberseguridad en hospitales y centros médicos.
-  Proporciona una base para cumplir con normativas regulatorias.
-  Minimiza el riesgo de brechas de datos y ataques cibernéticos.

###  TOGAF

-  Asegura la alineación de TI con los objetivos del negocio.
-  Mejora la gobernanza y la gestión de riesgos en la infraestructura de salud.
-  Facilita la planificación a largo plazo y la escalabilidad.

##  Proceso de Implementación

###  HL7/FHIR

1. Análisis de sistemas existentes y compatibilidad con HL7/FHIR.
2. Definición de protocolos de integración (mensajes HL7 o APIs FHIR).
3. Implementación de middleware de interoperabilidad.
4. Pruebas y certificación de interoperabilidad.
5. Despliegue y monitoreo continuo.

###  ISO 27799

1. Evaluación de riesgos de seguridad en salud.
2. Implementación de controles de acceso y cifrado.
3. Capacitación al personal en ciberseguridad.
4. Aplicación de monitorización y auditoría.
5. Cumplimiento con ISO 27001 y normativas locales.

###  TOGAF

1. Evaluación de la arquitectura empresarial actual.
2. Definición de la arquitectura objetivo alineada con los objetivos del negocio.
3. Diseño de hojas de ruta y planes de implementación.
4. Gestión del cambio y gobernanza durante el despliegue.
5. Monitoreo y actualización continua.

##  Comparación con BIAN y TOGAF

|  Característica | HL7    | FHIR   | ISO 27799 | BIAN   | TOGAF  |
|--------------------|--------|--------|----------|--------|--------|
| **Sector**         | Salud  | Salud  | Salud     | Banca  | Salud y otros |
| **Interoperabilidad**| Alta  | Muy Alta | Baja    | Alta (en banca) | Alta |
| **Seguridad de datos**| Media | Media | Alta     | Alta   | Media |
| **Regulación**     | Media  | Alta   | Muy Alta  | Alta   | Media |
| **Uso de APIs**    | No     | Sí     | No        | Sí     | No |
| **Enfoque**        | Mensajería clínica | APIs modernas | Seguridad en salud | Arquitectura bancaria | Arquitectura empresarial |

##  Conclusiones

-  HL7 y FHIR son fundamentales para la interoperabilidad en salud, mientras que ISO 27799 refuerza la ciberseguridad.
-  TOGAF proporciona una estructura para alinear TI con los objetivos estratégicos del sector salud.
-  FHIR es más flexible y moderno que HL7 v2, permitiendo una integración más eficiente.
-  ISO 27799 es clave para la gobernanza de datos y cumplimiento normativo.
-  BIAN no es adecuado para salud, pero su enfoque en arquitectura modular puede servir de referencia.

##  Recomendaciones

- ✔ Adoptar HL7 y FHIR para mejorar la interoperabilidad entre sistemas médicos.
- ✔ Implementar ISO 27799 para fortalecer la seguridad de la información de pacientes.
- ✔ Usar TOGAF para estructurar y alinear TI con los objetivos estratégicos de la organización.
- ✔ Combinar FHIR con arquitecturas modernas como microservicios y cloud computing.
- ✔ Realizar auditorías de seguridad periódicas para asegurar el cumplimiento con ISO 27799 y otras normativas.

---
#  Relación entre HL7 y FHIR

FHIR (Fast Healthcare Interoperability Resources) fue desarrollado por HL7 como una evolución de sus versiones anteriores (HL7 v2 y HL7 v3). La idea principal de FHIR es modernizar la interoperabilidad en salud usando tecnologías web como APIs RESTful, JSON y XML.

---

##  Diferencias Clave entre HL7 y FHIR

|  **Característica**   | **HL7 v2/v3**                                | **FHIR**                                |
|--------------------------|------------------------------------------|------------------------------------------|
| **Año de creación**         | HL7 v2 (1987), HL7 v3 (2005)              | FHIR (2014)                             |
| **Formato de datos**       | Mensajes delimitados por pipes (\`|\`) en v2, XML en v3 | JSON, XML, y otros formatos modernos    |
| **Modelo de comunicación** | Basado en mensajes (intercambio de archivos) | APIs RESTful (interacción directa con sistemas) |
| **Facilidad de implementación** | Complejo y requiere configuración específica | Más simple y modular                    |
| **Uso en la actualidad**   | Sigue siendo común en hospitales con sistemas antiguos | Preferido para nuevas implementaciones y apps móviles |
| **Flexibilidad**           | Rígido y estructurado                     | Modular y adaptable                      |
| **Integración con la nube** | Difícil                                    | Nativo para la nube                      |

---

## 📉 Conclusión

-  **HL7 v2** sigue siendo el estándar predominante en hospitales con infraestructura heredada.
-  **FHIR** es más moderno, flexible y fácil de integrar con nuevas tecnologías como la nube y la IA.
-  **FHIR** no reemplaza a HL7 v2/v3, sino que los complementa y facilita la transición hacia sistemas más interoperables.  

[GLOSARIO](./docs/glosario.md)
