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
