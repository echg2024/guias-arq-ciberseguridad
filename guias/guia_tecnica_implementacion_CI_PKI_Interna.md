# 🔐 Guía Técnica para la Implementación de una Infraestructura de Clave Pública (PKI) Interna en Entornos de Salud

## ¿Qué es una Autoridad Certificadora (CA) interna?

Una **CA interna** es una entidad dentro de una organización responsable de emitir, firmar, revocar y gestionar certificados digitales, utilizados principalmente para:

- 🔒 Cifrar comunicaciones internas (entre servidores, aplicaciones, bases de datos).
- 👤 Autenticar identidades de usuarios, servicios o dispositivos.
- 🔗 Establecer confianza dentro de una red privada.

> A diferencia de una CA pública (como DigiCert, Let’s Encrypt, etc.), una CA interna no es reconocida públicamente y está limitada al entorno de red de la organización.

---

## 🛡️ ¿Por qué implementar una CA interna?

1. ✅ Control total sobre certificados y políticas de emisión.
2. 🔐 Seguridad reforzada: evita depender de terceros.
3. 💰 Reducción de costos para grandes volúmenes de certificados.
4. 📜 Cumplimiento normativo y alineación con políticas corporativas.
5. 🔄 Soporte para mTLS en entornos Zero Trust o DevSecOps.

---

## 🧱 Componentes clave de una CA interna

- **Root CA**: Autoridad raíz que firma su propio certificado. Está aislada (offline) y es el pilar de confianza.
- **Intermediate CA**: Subordinada a la Root CA, emite certificados a usuarios y servicios.
- **Servidor de inscripción (Enrollment)**: Donde se solicitan y emiten los certificados.
- **CRL / OCSP**: Mecanismos para revocar y verificar el estado de los certificados.

---

## 🔧 Casos de uso típicos

- 🔐 Cifrado de tráfico interno con TLS/SSL.
- 🌐 VPNs y acceso remoto seguro.
- 📶 Autenticación de dispositivos IoT.
- ⚙️ Protección de APIs y microservicios con certificados mutuos.
- 🧾 Firmado de código interno o imágenes de contenedores.

---

## 🧩 Buenas prácticas

1. 📦 Mantén la **Root CA** offline y protegida.
2. ⏳ Aplica políticas de expiración y rotación de certificados.
3. 🤖 Automatiza el ciclo de vida del certificado (emisión, renovación, revocación).
4. 🏷️ Usa nombres DNS internos y **SANs** bien configurados.
5. 📈 Integra con sistemas de monitoreo para evitar expiraciones no planificadas.

---

## 📌 Diferencias: CA interna vs PKI interna

| Elemento                        | Descripción                                                                 |
|---------------------------------|-----------------------------------------------------------------------------|
| **CA interna**                  | Parte de la PKI. Emite, revoca y gestiona certificados.                     |
| **PKI interna**                 | Ecosistema completo: incluye Root/Intermediate CA, inscripción, CRL/OCSP, políticas, automatización y monitoreo. |

---

## 🧮 Modelos de Arquitectura PKI

| Modelo       | Ventajas                                                                 | Desventajas                                                                 | Recomendado para                                 |
|--------------|--------------------------------------------------------------------------|------------------------------------------------------------------------------|--------------------------------------------------|
| **Una capa** | - Fácil de implementar<br>- Bajo costo<br>- Administración sencilla      | - Menor seguridad (CA raíz expuesta)<br>- Punto único de fallo<br>- No escalable | 🧪 Laboratorios pequeños o entornos de prueba     |
| **Dos capas**| - Mayor seguridad (CA raíz offline)<br>- Escalable<br>- Buen manejo de revocaciones | - Más compleja que una capa<br>- Requiere mantenimiento de múltiples CAs    | 🏥 Organizaciones medianas/grandes del sector salud |
| **Tres capas**| - Máxima seguridad y segregación<br>- Alta escalabilidad<br>- Flexibilidad | - Mayor complejidad técnica<br>- Más costoso<br>- Requiere personal capacitado | 🏛️ Instituciones grandes o altamente reguladas    |

---

# 🔥 Recomendación

Si quieres un PKI interno completo, lo ideal es combinar herramientas:

- **EJBCA** o **Microsoft AD CS** como la CA principal.
- **HashiCorp Vault** o **CFSSL** para gestión de certificados en entornos dinámicos (cloud, microservicios).
- **OpenSSL** para pruebas y configuración manual inicial.

## 🔹 Arquitectura recomendada para tu PKI interno

### 🏢 Para Active Directory y Windows (infraestructura empresarial)
#### ✅ Microsoft AD CS
- Emite certificados para autenticación de usuarios, servidores y equipos en la red corporativa.
- Integración nativa con Windows y políticas de grupo.

### ☁️ Para cargas en GCP y microservicios
#### ✅ HashiCorp Vault + PKI Engine
- Ideal para certificados efímeros y automatización en entornos dinámicos.
- Se integra con Kubernetes, Terraform y CI/CD.
#### ✅ CFSSL (Cloudflare PKI Tool)
- Rápido y ligero para firmar certificados en pipelines de despliegue.
- Compatible con GCP Cloud Run y GKE.

### 🔑 Para gestión centralizada de la PKI
#### ✅ EJBCA
- Solución robusta con CA, CRL, OCSP y gestión de claves.
- Puede servir como la CA raíz de toda tu PKI interna.

### 🛠 Para administración manual y pruebas
#### ✅ OpenSSL
- Útil para crear certificados de prueba y debugging.
- Puede ser usado para firmar certificados en entornos offline.

---

## 📌 ¿Por qué comenzar con la CA interna antes de la PKI completa?

- Una **CA interna** es el núcleo de la **PKI** → Sin una CA bien definida, la infraestructura no tendrá base sólida.
- Te permite empezar con necesidades específicas → Emitir certificados para ciertos casos de uso antes de escalar a una PKI completa.
- Reduce complejidad inicial → Una PKI completa involucra múltiples componentes como CRL, OCSP, automatización, etc.
- Facilita pruebas y adopción interna → Implementar una CA interna primero permite validar procesos antes de extender la PKI a toda la organización.

---

## Arquitectura recomendada: Fase 1 - CA Interna

Para tu entorno híbrido (Windows, Linux y GCP Cloud), se recomienda comenzar con:

- **Root CA (offline)** → La autoridad certificadora raíz que firma certificados de CA intermedias.
- **Intermediate CA (online)** → Emite certificados para usuarios, servidores y aplicaciones.

### Herramientas recomendadas para esta fase:
- **Microsoft AD CS** → Para emitir certificados en la red interna (Windows).
- **EJBCA** o **HashiCorp Vault PKI** → Para Linux y microservicios en GCP.
- **OpenSSL** → Para la CA raíz offline y pruebas iniciales.

---

## Arquitectura recomendada: Fase 2 - PKI Interna Completa

Una vez que la CA interna esté operativa, puedes ampliar la arquitectura con:

- Gestión centralizada de certificados (EJBCA o HashiCorp Vault).
- Automatización con CFSSL o ACME (Let's Encrypt interno).
- Revocación de certificados (CRL y OCSP).
- Integración con Kubernetes y GCP IAM para emisión dinámica de certificados.

---

## 🧩 Cuadro de Riesgos y Tipos de Ataques – CA Interno vs PKI Interno

| Componente              | Riesgo por No Implementarlo                                       | Tipos de Ataques o Amenazas Asociadas                 | Impacto Potencial en el Sector Salud                              |
|-------------------------|------------------------------------------------------------------|------------------------------------------------------|------------------------------------------------------------------|
| **CA Interno (Autoridad Certificadora)** | - Falta de control sobre emisión de certificados. <br> - Uso de certificados autofirmados inseguros. <br> - Dificultad para revocar certificados comprometidos. | - Suplantación de servicios internos (MITM). <br> - Certificados falsos o no confiables. <br> - Falta de trazabilidad en accesos cifrados. | - Exposición de datos médicos (HIPAA / Ley de Protección de Datos). <br> - Pérdida de confianza en servicios digitales. <br> - Brechas de cumplimiento legal y auditoría. |
| **PKI Interno (Infraestructura de Clave Pública)** | - Imposibilidad de gestionar ciclo de vida de certificados. <br> - Sin autenticación fuerte de usuarios, apps, dispositivos. <br> - Uso débil de cifrado o claves compartidas. | - Ataques de phishing más efectivos por falta de identidad verificada. <br> - Accesos no autorizados a dispositivos IoT médicos o historias clínicas electrónicas. <br> - Exposición a ransomware por falta de autenticación mutua. | - Interrupción de servicios clínicos críticos. <br> - Robo de información sensible de pacientes. <br> - Posible multa y sanciones regulatorias. |

---

## 🛠️ Análisis de herramientas para construir un PKI interno

| Herramienta              | ¿Maneja CA? | ¿Gestión de Claves? | ¿Soporte CRL/OCSP? | ¿Automatizable? | ¿Casos de Uso?                            |
|-------------------------|-------------|---------------------|--------------------|-----------------|-------------------------------------------|
| **Microsoft AD CS**      | ✅ Sí       | ✅ Sí               | ✅ Sí              | ⚠️ Limitado     | Entornos Windows empresariales            |
| **HashiCorp Vault + PKI**| ✅ Sí       | ✅ Sí               | ❌ No (necesita addon) | ✅ Sí        | DevOps, Kubernetes, entornos híbridos     |
| **EJBCA**                | ✅ Sí       | ✅ Sí               | ✅ Sí              | ✅ Sí           | PKI completa y escalable                  |
| **OpenSSL**              | ✅ Sí       | ✅ Sí               | ❌ No (manual)     | ❌ No           | CA manual, laboratorio o pequeños entornos|
| **CFSSL (Cloudflare PKI)**| ✅ Sí       | ✅ Sí               | ❌ No (manual)     | ✅ Sí           | Microservicios, CI/CD                     |

---

## 1. Definir la estructura de la CA interna

- ¿Habrá una Root CA offline? (Recomendado para seguridad).
- ¿Cuántas Intermediate CAs se necesitarán? (Ejemplo: Una para Windows, otra para GCP).
- ¿Cómo se organizarán los certificados? (Usuarios, servidores, aplicaciones).

## 2. Estándares de seguridad para certificados

- Algoritmos de cifrado recomendados (Ejemplo: RSA-4096, ECC-P384).
- Períodos de validez de los certificados (Ejemplo: Root CA 10 años, Intermediate CA 5 años, Servidores 1 año).
- Requisitos de autenticación y emisión (¿Se requiere MFA para solicitar un certificado?).

## 3. Políticas de renovación y revocación

- ¿Cómo se manejará la expiración de certificados? (Automática o manual).
- ¿Cómo se revocarán certificados comprometidos? (CRL y OCSP).
- ¿Quién tiene autoridad para revocar certificados?

## 4. Integración con sistemas existentes

- **Microsoft AD CS** → Windows (autenticación, RADIUS, VPN, etc.).
- **GCP Cloud** → Certificados en Kubernetes (GKE) y servicios internos.
- **Linux** → Integración con servidores y microservicios.

## 5. Automatización y monitoreo

- ¿Se automatizará la emisión de certificados? (CFSSL, HashiCorp Vault).
- ¿Se integrará con herramientas de monitoreo? (Ejemplo: Prometheus, ELK, SIEM).

---

## 🧩 ¿Cuándo debes incluir un Key Vault en una PKI o CA interna?

| Momento o Componente               | ¿Usar Key Vault? | ¿Por qué? / Beneficio                                           |
|------------------------------------|------------------|---------------------------------------------------------------|
| Creación de la clave raíz (Root CA) | Sí, obligatorio  | Protege la clave más sensible del sistema. Evita extracción o uso indebido. |
| Emisión de certificados desde la SubCA | Sí, recomendable | Protege las claves privadas de la SubCA; reduce riesgo de compromisos. |
| Almacenamiento de claves privadas de dispositivos | Sí, opcional     | Si los dispositivos (como servidores, apps, equipos médicos) usan claves privadas que deben estar cifradas y auditadas. |
| Automatización de renovación de certificados | Sí, con integración | Un key vault moderno permite renovación y entrega automática sin exponer la clave. |
| Auditoría y cumplimiento regulatorio | Sí, importante   | Provee logs y control de acceso con MFA, RBAC, etc.             |

---

## 🏥 Arquitectura de PKI Interno y CA Interno con Key Vault - Sector Salud

1. **Nivel de Autoridades de Certificación (CA)**  
   - **Root CA (Offline)**: Almacenado en entorno desconectado.  
   - **Subordinate CA (Online)**: Emite certificados a dispositivos, usuarios y sistemas.

2. **Key Vault (Almacenamiento Seguro)**  
   - **Key Vault**: Almacenamiento seguro de claves privadas, certificados y secretos.

3. **Sistemas Clínicos (consumidores de certificados)**  
   - **EMR / HIS / PACS / LIMS / IoT Dispositivos Médicos**: Solicitan y usan certificados para cifrado TLS/SSL, autenticación mutua, y firma digital.

4. **Usuarios internos**  
   - **Usuarios Administrativos y Clínicos**: Usan certificados para autenticación y firma digital de documentos médicos.

5. **Consola de Administración de CA**  
   - **CA Management Console**: Usado por personal de TI para emitir, revocar y auditar certificados.

---

## 🏥 Recomendación para sector salud:

Para clínicas, hospitales o instituciones con sistemas críticos y cargas en la nube, el modelo de dos capas es el más balanceado, combinando seguridad, escalabilidad y control sin una complejidad extrema.

Si tu institución tiene múltiples sedes, servicios en nube, historia clínica electrónica, dispositivos médicos integrados, y debe cumplir regulaciones estrictas (como HIPAA, ISO 27799, etc.), considera evolucionar a un modelo de tres capas a mediano plazo.

**Referencias:**
- [Ahasayen](https://blog.ahasayen.com/how-to-design-a-pki-hierarchy/)
- [DigiCert](https://www.digicert.com/blog/how-to-build-a-pki-that-scales-hosted-versus-internal)
- [Keyfactor](https://docs.keyfactor.com/ejbca/latest/ejbca-architecture)
- [Microsoft Learn](https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/pki-design-considerations)

