# **GUÍA TÉCNICA PARA LA PROTECCIÓN DE DATOS SENSIBLES**

## **1. INTRODUCCIÓN** 
La presente guía técnica tiene como objetivo definir y estandarizar las mejores prácticas para la protección de datos sensibles en la clínica. Estas medidas ayudarán a garantizar la seguridad de la información en cumplimiento con las normativas aplicables y los lineamientos de seguridad.
Asimismo, se brindará los requisitos técnicos para el uso adecuado de mecanismos criptográficos dentro de la clínica, con el fin de garantizar la confidencialidad, integridad y autenticidad de los datos sensibles y la información institucional.

## **2. OBJETIVO**
Brindar una referencia técnica clara sobre los mecanismos de protección de datos, incluyendo cifrado, tokenización, ofuscamiento y otras técnicas de seguridad y definir los algoritmos, protocolos y configuraciones criptográficas aceptadas y prohibidas en los sistemas de información de la clínica.

## **3. Alcance**
Este lineamiento aplica a todos los sistemas, aplicaciones, bases de datos, dispositivos y servicios que utilicen criptografía dentro del entorno tecnológico de la clínica, tanto internos como externos.

## **4. TÉCNICAS DE PROTECCIÓN DE DATOS**

### **4.1 Cifrado (Encryption)**
Convierte datos en un formato ilegible sin una clave de descifrado.
El cifrado es esencial para proteger datos sensibles como historias clínicas electrónicas (HCE), diagnósticos, tratamientos, y cualquier tipo de información que se maneje en sistemas de gestión hospitalaria. El uso de cifrado en reposo y en tránsito garantiza que los datos sean accesibles solo para personal autorizado.


| Tipo de Cifrado | Uso Recomendado | Ejemplo de Aplicación |
|----------------|----------------|------------------------|
| **AES-256** | Datos en reposo | Bases de datos, discos duros, backups |
| **TLS 1.2 / 1.3** | Datos en tránsito | Comunicación entre sistemas, APIs, acceso remoto |
| **RSA-4096** | Claves y certificados | Firma digital, certificados SSL/TLS |
| **SHA-256 / SHA-512** | Hashing de contraseñas | Almacenamiento seguro de credenciales |
| **ECC (Elliptic Curve Cryptography)** | Alternativa ligera a RSA | Dispositivos IoT, certificados en sistemas embebidos |

**Ejemplo de uso:** 
- Cifrado de bases de datos que contienen información sobre pacientes, diagnósticos, tratamientos y recetas médicas.

### **🏷️4.2 Tokenización (Tokenization)**
Reemplaza datos sensibles con un valor alternativo (token), sin relación matemática con el dato original.

La tokenización es especialmente útil para proteger datos de pago o cualquier información sensible que pueda ser almacenada o procesada, como números de tarjetas de seguro o identificadores personales.

**Ejemplos de uso:**
- Reemplazar el número de seguridad social o el número de tarjeta de seguro médico con un token, evitando su exposición en sistemas de pago.
- Protección de números de tarjetas de crédito.
- Almacenamiento seguro de identificadores personales en bases de datos.

### **🏷️4.3 Ofuscamiento (Obfuscation)**
Transforma datos en un formato menos inteligible sin alterar su estructura, evitando su comprensión directa.

El ofuscamiento de datos puede ser utilizado en entornos de desarrollo y pruebas, donde se requiere trabajar con datos de pacientes pero sin revelar su identidad completa.

**Ejemplos de uso:**
- Ocultación de direcciones de correo electrónico en plataformas públicas.
- Protección del código fuente en software.
- Ocultar la información sensible de pacientes en bases de datos utilizadas en pruebas de software o en demostraciones públicas.

### **🏷️4.4 Hashing**
Convierte datos en una huella digital irreversible y única.
El hashing es muy útil para almacenar contraseñas de acceso a sistemas de información de salud sin exponerlas directamente. Además, es útil para garantizar la integridad de los datos mediante la verificación de su huella digital.

| Algoritmo | Uso Recomendado |
|-----------|----------------|
| **SHA-256 / SHA-512** | Contraseñas seguras |
| **HMAC (Hash-based Message Authentication Code)** | Autenticación de mensajes |
| **BCrypt / Argon2** | Protección de credenciales |

**Ejemplos de uso:**
- Hashing de contraseñas de acceso a registros de salud electrónicos y autenticación de usuarios.

### **🏷️4.5 Enmascaramiento de Datos (Data Masking)**
Oculta parcialmente la información sensible para reducir el riesgo de exposición.
El enmascaramiento de datos es importante para proteger la información sensible en entornos de prueba y desarrollo, asegurando que no se exponga información real de los pacientes.

**Ejemplos de uso:**
- Al trabajar con datos de pacientes en pruebas de sistemas, se pueden enmascarar identificadores personales, diagnósticos o resultados de laboratorio.
- Enmascaramiento de Números de Tarjeta de Crédito: 4111-XXXX-XXXX-1234
- Anonimización de datos en entornos de prueba.

### **🏷️4.6 Anonimización de Datos (Data Anonymization)**
Transforma datos de manera irreversible para evitar la identificación de individuos.
La anonimización es clave para la investigación y el análisis de grandes volúmenes de datos médicos, donde se necesita trabajar con datos de pacientes pero sin revelar su identidad. Es crucial para cumplir con las regulaciones como la HIPAA en EE. UU. o la Ley de Protección de Datos Personales en Perú (Ley N° 29733).

**Ejemplos de uso:**
- Anonimización de datos de pacientes para estudios epidemiológicos o investigaciones científicas.
- Eliminación de identificadores personales en registros médicos.
- Generalización de datos en estudios estadísticos.

### **🏷️4.7 Fragmentación y Dispersión de Datos (Data Sharding/Splitting)**
Divide datos en múltiples partes distribuidas en diferentes ubicaciones para reducir el riesgo de acceso no autorizado.
En algunos casos, fragmentar y distribuir los datos de forma segura entre diferentes servidores puede ser útil para asegurar que, incluso si un servidor se ve comprometido, los datos no estén completos y sean accesibles de manera segura.

**Ejemplo de uso:**
- Dividir bases de datos entre diferentes servidores para que la información no se almacene en un solo lugar, reduciendo el riesgo de exposición masiva de datos.
- Bases de datos distribuidas en múltiples servidores con acceso restringido.

## **📋5. CIFRADO Y PROTOCOLOS DE SEGURIDAD**
Este capítulo detalla los algoritmos y protocolos de cifrado que deben ser desautorizados debido a sus riesgos de seguridad, así como aquellos que se deben utilizar para garantizar la protección de los datos. A continuación, se especifican los protocolos, algoritmos de cifrado, funciones hash y algoritmos de firma que deben evitarse o adoptarse conforme a las mejores prácticas y estándares de seguridad internacionales.

| **Ciphers y Protocolos** | **Estado**     | **Descripción**                                             |
|--------------------------|----------------|-------------------------------------------------------------|
| **Protocolos**            |                |                                                             |
| SSL 2.0                  | Desautorizado  | Protocolo obsoleto con vulnerabilidades conocidas.           |
| SSL 3.0                  | Desautorizado  | Protocolo obsoleto con vulnerabilidades conocidas.           |
| TLS 1.0                  | Desautorizado  | Protocolo obsoleto con vulnerabilidades conocidas.           |
| TLS 1.1                  | Desautorizado  | Protocolo obsoleto con vulnerabilidades conocidas.           |
| TLS 1.2                  | Permitido      | Protocolo seguro y ampliamente utilizado.                    |
| TLS 1.3                  | Permitido      | Última versión del protocolo TLS con mejoras de seguridad.   |
| **Algoritmos de Cifrado**|                |                                                             |
| RC4                      | Desautorizado  | Algoritmo de cifrado con debilidades de seguridad.           |
| DES                      | Desautorizado  | Algoritmo de cifrado obsoleto con clave débil.               |
| 3DES                     | Desautorizado  | Algoritmo de cifrado con vulnerabilidades conocidas.         |
| AES-128-GCM              | Permitido      | Algoritmo de cifrado moderno y recomendado.                  |
| AES-256-GCM              | Permitido      | Algoritmo de cifrado moderno y recomendado.                  |
| ChaCha20-Poly1305        | Permitido      | Algoritmo de cifrado recomendado para entornos modernos.     |
| **Funciones Hash**       |                |                                                             |
| MD5                      | Desautorizado  | Función hash vulnerable a colisiones.                        |
| SHA-1                    | Desautorizado  | Función hash con debilidades conocidas.                      |
| SHA-256                  | Permitido      | Función hash recomendada con alta seguridad.                 |
| SHA-384                  | Permitido      | Función hash recomendada con alta seguridad.                 |
| **Algoritmos de Firma**  |                |                                                             |
| RSA (>=2048 bits)        | Permitido      | Algoritmo de firma recomendado con seguridad fuerte.         |
| ECDSA                    | Permitido      | Algoritmo de firma recomendado con seguridad fuerte.         |
| Ed25519                  | Permitido      | Algoritmo de firma recomendado con seguridad fuerte.         |
| **Otros**                |                |                                                             |
| NULL encryption          | Desautorizado  | Cifrado sin encriptación, vulnerable a ataques.              |
| EXPORT ciphers           | Desautorizado  | Cifrados con clave débil, vulnerables a ataques.             |


## **📋6. RECOMENDACIONES PARA SU IMPLEMENTACIÓN**
- Definir claramente los tipos de datos que deben protegerse.
- Implementar cifrado obligatorio en todas las bases de datos y sistemas críticos.
- Utilizar autenticación multifactor (MFA) para el acceso a información sensible.
- Aplicar políticas de retención y eliminación segura de datos.
- Monitorear accesos y posibles vulnerabilidades de manera continua.
- Capacitar al personal sobre las mejores prácticas de seguridad de la información.

## **🔄7. REVISIÓN Y ACTUALIZACIÓN**
Esta guía deberá revisarse y actualizarse periódicamente para reflejar cambios en normativas, tecnología y mejores prácticas de seguridad.

---
**Fecha de emisión:** [DD/MM/AAAA]  
**Responsables:**  
[Nombre del Responsable de TI] – Departamento de TI  
[Nombre del Oficial de Protección de Datos] – Oficial de Protección de Datos
