# Configuración de red y conectividad en Ubuntu Server

## 1. Descripción del módulo

Este módulo documenta la configuración y administración de la conectividad de red en Ubuntu Server dentro de un entorno virtualizado con Oracle VirtualBox.

Se realizan comprobaciones de interfaces de red, direccionamiento IP, configuración DNS, tabla de rutas, conectividad a Internet y acceso remoto mediante SSH.

**Sistema operativo:** Ubuntu Server 26.04.1 LTS 
**Servidor:** `cloud-server-administration-lab`  
**Usuario administrador:** `cloud-server`  
**Virtualización:** Oracle VirtualBox  
**Adaptador de red:** NAT

## 2. Objetivos

- Identificar las interfaces de red disponibles.
- Consultar la dirección IPv4 asignada al servidor.
- Revisar la puerta de enlace y la tabla de rutas.
- Verificar la resolución DNS.
- Comprobar la conectividad con Internet.
- Validar el acceso remoto mediante SSH.
- Documentar la configuración de red del laboratorio.

## 3. Identificación de interfaces de red

Consultar las interfaces disponibles:

```bash
ip link show
```

Consultar las direcciones IP asignadas:

```bash
ip -br addr
```

Mostrar información detallada:

```bash
ip addr show
```

## 4. Configuración IP y rutas

Consultar la tabla de rutas:

```bash
ip route
```

Consultar la ruta utilizada para alcanzar una dirección externa:

```bash
ip route get 8.8.8.8
```

Identificar la puerta de enlace predeterminada:

```bash
ip route | grep default
```

## 5. Configuración DNS

Consultar los servidores DNS utilizados por el sistema:

```bash
resolvectl status
```

Consultar la configuración DNS resumida:

```bash
cat /etc/resolv.conf
```

Comprobar la resolución de nombres:

```bash
getent hosts google.com
```

## 6. Pruebas de conectividad

### 6.1. Comprobar conectividad con la puerta de enlace

Identificar primero la dirección de la puerta de enlace mediante `ip route`.

Después ejecutar, sustituyendo la dirección por la que aparezca en tu sistema:

```bash
ping -c 4 DIRECCION_DE_LA_PUERTA_DE_ENLACE
```

### 6.2. Comprobar conectividad externa por IP

```bash
ping -c 4 8.8.8.8
```

### 6.3. Comprobar conectividad mediante DNS

```bash
ping -c 4 google.com
```

La comparación de las pruebas permite distinguir problemas de conectividad IP de problemas de resolución DNS.

## 7. Configuración de red en VirtualBox

La máquina virtual utiliza un adaptador de red configurado en modo NAT.

En este modo, VirtualBox permite que el sistema invitado utilice la conectividad del equipo anfitrión.

El acceso a servicios específicos del invitado puede realizarse mediante reglas de reenvío de puertos.

Configuración utilizada para este laboratorio:

| Servicio | Puerto del host | Puerto del invitado |
|---|---:|---:|
| SSH | 2222 | 22 |
| HTTP | 8080 | 80 |

La dirección `127.0.0.1` representa el equipo anfitrión cuando se accede a estos servicios desde Windows.

## 8. Validación de SSH

Comprobar el estado del servicio:

```bash
systemctl is-active ssh
```

Consultar el puerto en escucha:

```bash
sudo ss -tulpn | grep ':22'
```

Comprobar la configuración efectiva de seguridad SSH:

```bash
sudo sshd -T | grep -E 'permitrootlogin|pubkeyauthentication|passwordauthentication|kbdinteractiveauthentication'
```

La configuración esperada del laboratorio es:

```text
permitrootlogin no
pubkeyauthentication yes
passwordauthentication no
kbdinteractiveauthentication no
```

La conexión desde Windows se realiza utilizando el puerto reenviado de VirtualBox:

```powershell
ssh -i "$env:USERPROFILE\.ssh\id_ed25519" -p 2222 cloud-server@127.0.0.1
```

## 9. Validación del servicio HTTP

Comprobar que el servidor web responde localmente:

```bash
curl -I http://localhost
```

Desde Windows, utilizando el reenvío de puertos de VirtualBox:

```text
http://127.0.0.1:8080
```

Una respuesta HTTP `200 OK` confirma que el servidor web está respondiendo correctamente.

## 10. Resultados obtenidos

Esta sección se completará con los resultados reales de las pruebas de interfaces, direccionamiento IP, rutas, DNS, conectividad y acceso SSH.

## 11. Evidencias del laboratorio

Las capturas se almacenarán en:

```text
evidence/03-red-conectividad/
```

### 11.1. Interfaces de red

![Interfaces de red](../evidence/03-red-conectividad/01-interfaces-red.png)

### 11.2. Direccionamiento IP

![Direccionamiento IP](../evidence/03-red-conectividad/02-direccionamiento-ip.png)

### 11.3. Tabla de rutas

![Tabla de rutas](../evidence/03-red-conectividad/03-tabla-rutas.png)

### 11.4. Configuración DNS

![Configuración DNS](../evidence/03-red-conectividad/04-configuracion-dns.png)

### 11.5. Pruebas de conectividad

![Pruebas de conectividad](../evidence/03-red-conectividad/05-pruebas-conectividad.png)

### 11.6. Configuración SSH

![Configuración SSH](../evidence/03-red-conectividad/06-configuracion-ssh.png)

### 11.7. Acceso HTTP

![Acceso HTTP](../evidence/03-red-conectividad/07-acceso-http.png)

## 12. Conclusión

La práctica permite comprender la configuración de red de un servidor Ubuntu virtualizado, identificar sus interfaces y direcciones IP, verificar la resolución DNS y comprobar la conectividad.

También permite documentar el acceso remoto mediante SSH y la publicación del servicio web a través de las reglas de reenvío de puertos de VirtualBox.

Estas habilidades son fundamentales para la administración de servidores Linux, la infraestructura de red y los entornos cloud.