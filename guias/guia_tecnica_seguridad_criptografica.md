# **GUÍA DE SEGURIDAD CRIPTOGRÁFICA**

---

## **1. Introducción**
Este lineamiento establece los requisitos técnicos para el uso adecuado de mecanismos criptográficos dentro de la clínica, con el fin de garantizar la confidencialidad, integridad y autenticidad de los datos sensibles y la información institucional.

## **2. Objetivo**
Definir los algoritmos, protocolos y configuraciones criptográficas aceptadas y prohibidas en los sistemas de información de la clínica.

## **3. Alcance**
Este lineamiento aplica a todos los sistemas, aplicaciones, bases de datos, dispositivos y servicios que utilicen criptografía dentro del entorno tecnológico de la clínica, tanto internos como externos.

## **4. Ciphers Deprecados (Prohibidos)**
Los siguientes algoritmos y protocolos están desautorizados por representar riesgos de seguridad:

- **Protocolos**: SSL 2.0, SSL 3.0, TLS 1.0, TLS 1.1
- **Algoritmos de cifrado**: RC4, DES, 3DES
- **Funciones hash**: MD5, SHA-1
- **Ciphers** con NULL encryption, EXPORT ciphers

## **5. Ciphers Permitidos y Recomendados**
Se deberán utilizar algoritmos y protocolos actualizados y validados por estándares internacionales:

- **Protocolos**: TLS 1.2, TLS 1.3
- **Algoritmos de cifrado**: AES-128-GCM, AES-256-GCM, ChaCha20-Poly1305
- **Funciones hash**: SHA-256, SHA-384
- **Algoritmos de firma**: RSA (>=2048 bits), ECDSA, Ed25519

## **6. Configuración de uso criptográfico**
- La configuración por defecto de servidores y aplicaciones deberá priorizar los ciphers más robustos.
- Está prohibido el uso de certificados autofirmados para entornos productivos.
- Las claves deben tener un periodo de rotación definido (según criticidad y tipo).

## **7. Requisitos para la Autoridad Certificadora Interna (CA/PKI)**
- Los certificados deben emitirse con una longitud de clave mínima de 2048 bits.
- La infraestructura PKI deberá mantener registros de emisión y revocación.
- Se deben definir perfiles de certificados según el uso (servidores, usuarios, dispositivos).

## **8. Revisión y Actualización**
Este lineamiento debe revisarse anualmente o cuando existan actualizaciones críticas en los estándares internacionales (NIST, ISO, IETF).

## **9. Referencias**
- NIST SP 800-52 Rev. 2
- NIST SP 800-131A Rev. 2
- ISO/IEC 27002:2022
- OWASP Cheat Sheets: Cryptographic Storage, Transport Layer Protection

## **10. Aprobación**
Este lineamiento será aprobado por el Comité de Seguridad de la Información de la clínica y tendrá carácter obligatorio para todas las áreas tecnológicas.
