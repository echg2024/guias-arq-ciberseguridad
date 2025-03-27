# 🔍 Herramientas de Seguridad en Red y Vulnerabilidades

## 🔹 1. Nmap / Masscan → Escaneo de Red y Puertos

### 📌 Instalación en Kali Linux / Ubuntu / Debian:
```bash
sudo apt update && sudo apt install nmap masscan -y
```

### 📌 Instalación en Windows (PowerShell como Administrador):
1. Descarga el instalador de Nmap: [Nmap Download](https://nmap.org/download.html)
2. Instala el paquete y asegúrate de incluir Zenmap (versión GUI).
3. Para Masscan en Windows, usa WSL (Windows Subsystem for Linux) e instala con:

```bash
sudo apt install masscan -y
```

### 📌 Verifica la instalación:
```bash
nmap --version
masscan --version
```

---

## 🔹 2. Nessus / OpenVAS → Escaneo de Vulnerabilidades

### 📌 Instalación de Nessus en Kali Linux / Ubuntu / Debian:
1. Descarga el instalador desde [Tenable Nessus](https://www.tenable.com/downloads/nessus)
2. Instala el paquete:

```bash
sudo dpkg -i Nessus-*.deb
sudo systemctl start nessusd
```

3. Accede a Nessus en el navegador: [https://localhost:8834](https://localhost:8834)
4. Regístrate y activa el producto con la clave de Tenable.

### 📌 Instalación de OpenVAS (Alternativa Gratuita) en Kali Linux:
```bash
sudo apt update && sudo apt install openvas -y
sudo openvas-setup
```

### 📌 Accede en el navegador: [https://127.0.0.1:9392](https://127.0.0.1:9392)

---

## 🔹 3. BloodHound → Análisis de Active Directory

### 📌 Instalación en Kali Linux / Ubuntu:
```bash
sudo apt update && sudo apt install bloodhound -y
sudo neo4j console
```

### 📌 Ejecuta BloodHound:
```bash
bloodhound
```

### 🔹 Para Windows: 
Usa el instalador desde GitHub: [BloodHound Releases](https://github.com/BloodHoundAD/BloodHound/releases)

---

## 🔹 4. Metasploit Framework → Explotación de Vulnerabilidades

### 📌 Instalación en Kali Linux / Ubuntu / Debian:
```bash
sudo apt update && sudo apt install metasploit-framework -y
```

### 📌 Inicia Metasploit:
```bash
msfconsole
```

### 📌 Si usas Windows, descarga desde: [Metasploit Download](https://www.metasploit.com/download)

---

## 🔹 5. Shodan / Censys → Identificación de Dispositivos Médicos

### 📌 Instalación en Kali Linux / Ubuntu / Windows:

1. Instala Python 3 y pip:
```bash
sudo apt update && sudo apt install python3 python3-pip -y
```

2. Instala la CLI de Shodan y Censys:
```bash
pip3 install shodan censys
```

3. Configura la API de Shodan (necesitas una cuenta en [Shodan](https://shodan.io)):
```bash
shodan init TU_API_KEY
```

### 📌 Ejemplo de búsqueda de servidores PACS en Perú:
```bash
shodan search "PACS country:PE"
```
---
## 🚀 Conclusión
Una vez instaladas estas herramientas, puedes empezar a probarlas en entornos controlados.

- ✅ **Nmap / Masscan** → Instalados con `apt install`
- ✅ **Nessus / OpenVAS** → Descarga manual e instalación
- ✅ **BloodHound** → Instalado con `apt install`
- ✅ **Metasploit** → Instalado con `apt install`
- ✅ **Shodan / Censys** → Instalado con `pip install


---
# 🚨 Recomendación para Entornos Corporativos de Salud en Perú 🚨

En una empresa del sector salud en Perú, donde la ciberseguridad y la protección de datos son críticas (especialmente por normativas como la **Ley de Protección de Datos Personales - Ley N° 29733**), **NO** es recomendable instalar herramientas de pentesting en tu laptop corporativa.

## ✅ Motivos para Exigir un Equipo Dedicado para Pentesting

### Evitar Conflictos con Políticas de Seguridad Interna:
- Muchas empresas tienen controles de **Endpoint Detection and Response (EDR)** como **CrowdStrike**, **Microsoft Defender ATP** o **SentinelOne**, que pueden bloquear herramientas de pentesting por considerarlas maliciosas.
- Instalar estas herramientas en tu laptop corporativa podría activar alertas y causar problemas con el equipo de IT o SOC.

### Minimizar Riesgos de Exposición de Datos Sensibles:
- Las herramientas de pentesting pueden almacenar logs con información de la red corporativa, lo que podría generar riesgos en caso de incidentes o auditorías.

### Evitar Sanciones o Problemas Legales:
- El sector salud maneja datos sensibles de pacientes y cualquier actividad de prueba no autorizada puede interpretarse como una violación de regulaciones.
- La **Ley N° 29733** y la normativa de la **SBS** pueden sancionar el acceso no autorizado a datos personales.

### Mejor Gestión de Recursos y Rendimiento:
- Herramientas como **Metasploit**, **Nessus** o **OpenVAS** consumen mucha **RAM** y **CPU**, lo que podría ralentizar tu laptop corporativa y afectar tu productividad.

## 📌 ¿Qué Solicitar a la Empresa?

Para un entorno seguro y controlado, debes pedir un equipo dedicado con las siguientes características:

- ✔ **Laptop o Servidor Virtual (VM)** con **Kali Linux** o **Parrot OS**
- ✔ **Acceso restringido a una red de pruebas aislada**
- ✔ **Autorización explícita del área de seguridad/cumplimiento**
- ✔ **Instalación de herramientas en una máquina virtual separada**

## ⚡ Alternativas: Uso de Laboratorios en la Nube

Si la empresa no puede proporcionarte un equipo físico, puedes sugerir el uso de:

- 🔹 **TryHackMe** / **Hack The Box** → Para entrenar pentesting sin riesgos
- 🔹 **AWS** / **Azure** / **GCP** → Para crear entornos de prueba controlados
- 🔹 **Proxmox** / **VMware ESXi** → Para correr máquinas virtuales localmente

## 🔴 ¡IMPORTANTE!

Antes de hacer pentesting en el entorno de la empresa, **obtén siempre una autorización formal** del **CISO** o del área de seguridad.

## 📢 Conclusión:

- ✅ No instales herramientas de pentesting en tu laptop corporativa.
- ✅ Solicita un equipo dedicado o un entorno virtual.
- ✅ Cumple con normativas de seguridad del sector salud en Perú.
- ✅ Usa entornos en la nube o laboratorios controlados para entrenar.
