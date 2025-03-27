# 🔒 Guía Integral de Preparación y Respuesta ante Ransomware en el Sector Salud

## 📊 Acciones Inmediatas para Comenzar
- ✅ **Realiza un diagnóstico inicial de riesgos.**
- 🎓 **Diseña un plan de capacitación para la gerencia.**
- 📜 **Desarrolla y aprueba las políticas de respuesta ante ransomware.**
- 🛠️ **Implementa pruebas de restauración y simulaciones de incidentes.**
- ✈️ **Actualiza el plan según lecciones aprendidas.**

---

## 📈 Desarrollo

### 1. 🔍 Evaluación y Diagnóstico Inicial
- **Evaluación de Riesgos:**
  - ☑️ Análisis de vulnerabilidades y assessment de riesgos enfocado en ransomware.
  - 🛠️ Identificación de sistemas críticos (PHI, EHR).
  - 🔔 Evaluación de vectores de ataque (phishing, RDP, vulnerabilidades no parchadas).

- **Clasificación de Datos y Sistemas:**
  - 🗳️ Prioriza datos confidenciales y sistemas esenciales para la continuidad del servicio de salud.

---

### 2. 📝 Concienciación y Capacitación del Personal de Gerencia
- **Capacitación para la Alta Dirección:**
  - 📈 Impacto financiero y legal del ransomware en el sector salud.
  - 🔑 Roles y responsabilidades en caso de un ataque.
  - 🛠️ Importancia de respaldos y políticas de ciberseguridad.

- **Simulaciones de Incidentes (Tabletop Exercises):**
  - 🎮 Simulaciones para liderazgo y gestión de crisis.
  - ⚡️ Evaluación de toma de decisiones bajo presión y coordinación técnica.

---

### 3. 🛠️ Desarrollo de Políticas y Lineamientos Específicos
- **Política de Respuesta ante Ransomware:**
  - 📆 Establece qué hacer y quién hace qué en cada etapa del ataque.
  - 📝 Criterios para notificar a las autoridades y a los afectados.

- **Política de Respaldo y Restauración:**
  - 💾 Especifica frecuencia de backups y ubicación (on-premises y cloud).
  - ⚖️ Asegura pruebas periódicas y copias desconectadas (air-gapped).

- **Política de Actualización y Parches:**
  - 🌟 Plazos claros para parchar vulnerabilidades críticas.
  - 🔧 Plan de actualización para hardware y software médico.

---

### 4. 🔒 Prevención y Fortalecimiento de la Postura de Seguridad

- **Chequeo de Salud y Seguridad de Active Directory (AD):**
  - 🔎 Revisar replicación y errores en controladores de dominio.
  - 🛠️ Identificar cuentas con privilegios excesivos y eliminar accesos no necesarios.
  - 🔐 Revisar contraseñas antiguas o cuentas inactivas.
  - ⚖️ Evaluar políticas de seguridad como bloqueos de cuentas y contraseñas complejas.
  - 🛠️ Revisar cambios recientes y asegurar la integridad de GPOs críticas.
  - 📊 Revisar eventos sospechosos, accesos inusuales y fallos de inicio de sesión.
  - 🛠️ Asegurarse de que el sistema operativo y el software del AD estén actualizados.

- **Autenticación y Acceso:**
  - 🔒 Implementar MFA para accesos remotos y sistemas críticos.
  - ⚠️ Limitar protocolos inseguros como RDP.

- **Protección de Endpoints y Redes:**
  - 🛡️ Soluciones EDR/XDR y segmentación de red.
  - 📶 Monitoreo y bloqueo de actividades sospechosas.

- **Phishing y Concienciación del Usuario:**
  - 💼 Capacitar regularmente y realizar simulaciones de phishing.

---

## 📃 Referencias

- [INCIBE](./docs/guia_ransomware.pdf)
- [Cybersecurity and Infrastructure Security Agency (CISA)](https://www.cisa.gov/sites/default/files/publications/CISA_MS-ISAC_Ransomware_Guide_S508C.pdf)
- [National Institute of Standards and Technology (NIST)](https://csrc.nist.gov/publications/detail/sp/1800-26/final)
- [Health Sector Cybersecurity Coordination Center (HC3)](https://www.hhs.gov/sites/default/files/ransomware-trends-2021.pdf)
- [Microsoft Security Intelligence](https://www.microsoft.com/security/blog)
- [European Union Agency for Cybersecurity (ENISA)](https://www.enisa.europa.eu/publications/threat-landscape-for-ransomware-attacks)
- [Verizon Data Breach Investigations Report (DBIR) 2023](https://www.verizon.com/business/resources/reports/dbir/)
- [IBM Security - Cost of a Data Breach Report 2022](https://www.ibm.com/security/data-breach)
- [Kaspersky Lab - Ransomware Attacks in Healthcare](https://www.kaspersky.com/resource-center/threats/ransomware)
- [Instituto Nacional de Defensa de la Competencia y de la Protección de la Propiedad Intelectual (INDECOPI) - Buenas Prácticas en Seguridad de la Información y Protección de Datos](https://www.indecopi.gob.pe/)
- [International Association of Privacy Professionals (IAPP) - Legal Implications of Ransomware and Data Breaches in Healthcare](https://iapp.org/)

