# **LINEAMIENTOS PARA LA IMPLEMENTACIÓN Y GESTIÓN DE UNA CA INTERNA Y PKI INTERNA EN EL SECTOR SALUD**

---

## **1. Introducción**

En el sector salud, la protección de la información es fundamental para garantizar la confidencialidad, integridad y disponibilidad de los datos sensibles de los pacientes y de la infraestructura hospitalaria. La implementación de una Infraestructura de Clave Pública (PKI) interna, respaldada por una Autoridad Certificadora (CA) interna, permite cifrar las comunicaciones, autenticar usuarios y dispositivos, y garantizar la trazabilidad de las transacciones digitales. Este documento establece los lineamientos para la implementación y gestión segura de una CA interna y una PKI interna en el sector salud.

---

## **2. Objetivo**

Definir los principios, controles de seguridad y procedimientos requeridos para la implementación y administración de una CA interna y PKI interna en el sector salud, garantizando el cumplimiento de normativas y mejores prácticas de ciberseguridad.

---

## **3. Alcance**

Este documento aplica a todas las entidades del sector salud que requieran una PKI interna para la emisión y gestión de certificados digitales, incluyendo hospitales, clínicas, laboratorios y proveedores de servicios médicos. Abarca la implementación, configuración, administración y auditoría de la CA interna y PKI interna.

---

## **4. Marco Regulatorio y Normativo**

La implementación de una PKI interna debe alinearse con las siguientes normativas y estándares:
- **ISO 27001**: Gestión de seguridad de la información.
- **ISO 27799**: Seguridad de la información en salud.
- **NIST SP 800-57**: Recomendaciones para la gestión de claves criptográficas.
- **NIST SP 800-63**: Directrices para la identidad digital.
- **HL7 y FHIR**: Interoperabilidad de datos en salud.
- **Regulaciones locales del sector salud en materia de protección de datos personales**.

---

## **5. Principios de la CA Interna y PKI Interna**

1. **Confidencialidad**: Asegurar que la información cifrada solo sea accesible por entidades autorizadas.
2. **Integridad**: Garantizar la autenticidad y no alteración de los datos.
3. **Disponibilidad**: Asegurar la emisión y gestión de certificados de manera ininterrumpida.
4. **Trazabilidad**: Implementar auditorías y registros de actividades relacionadas con la PKI.
5. **Cumplimiento**: Adherencia a normativas y mejores prácticas.

---

## **6. Controles de Seguridad**

- **Uso de una CA Raíz offline** y CA intermedias online. [Guía Técnica Protección de Datos Sensibles](/guias-arq-ciberseguridad/guias/guia-tecnica-proteccion-datos.html)
- **Emisión de certificados con algoritmos seguros** (RSA 4096, ECC P-384). Para mayor información revisar la [Guía Técnica Protección de Datos Sensibles](/guias-arq-ciberseguridad/guias/guia-tecnica-proteccion-datos.html)
- **Periodo de validez y renovación**: Definición de tiempos según el tipo de certificado.
- **Revocación de certificados mediante CRL y OCSP**.
- **Autenticación multifactor (MFA) para administradores de la PKI**.
- **Monitoreo y auditoría de eventos en la PKI**.

---

## **7. Roles y Responsabilidades**

- **Administrador de PKI**: Gestiona la infraestructura y la emisión de certificados.
- **Oficial de Seguridad de la Información**: Supervisa el cumplimiento normativo.
- **Usuarios finales**: Utilizan los certificados para autenticación y cifrado.
- **Auditor de PKI**: Evalúa la seguridad y cumplimiento de los lineamientos.

---

## **8. Matriz RACI**

| Actividad | Administrador PKI | Oficial de Seguridad | Usuarios | Auditor |
|-----------|------------------|----------------------|---------|---------|
| Implementación de la CA | R | A | C | I |
| Emisión de certificados | R | A | C | I |
| Monitoreo de eventos | R | A | C | I |
| Auditoría de PKI | I | A | C | R |

(R: Responsable, A: Aprobador, C: Consultado, I: Informado)

---

## **9. Procedimientos Específicos**

- **Solicitud de certificados**: Formato y validación de identidad.
- **Renovación de certificados**: Política de notificación previa a vencimiento.
- **Revocación de certificados**: Procedimiento y lista de revocación.
- **Backup y recuperación de claves**: Plan de respaldo y restauración.
- **Monitoreo y auditoría**: Revisiones periódicas de logs y accesos.

---

## **10. Revisión y Mejora Continua**

- **Revisión anual** de los lineamientos.
- **Actualización de controles** basada en nuevas amenazas.
- **Capacitación continua** para usuarios y administradores.

---

## **11. Aprobación Formal**

Este documento debe ser aprobado por la Dirección de Seguridad de la Información y las unidades de cumplimiento normativo en el sector salud. Las actualizaciones deben ser validadas y autorizadas según el procedimiento interno establecido.

---

**Fecha de aprobación:** [DD/MM/AAAA]

**Firmas:**

[Nombre del Responsable de TI] – Departamento de TI 
[Nombre del Oficial de Protección de Datos] – Oficial de Protección de Datos 
[Nombre del Director de la Clínica] – Dirección General
