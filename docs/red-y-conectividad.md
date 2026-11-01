Red y acceso remoto SSH

## Objetivo
Verificar la configuración de red de Ubuntu Server y habilitar su administración remota desde Windows.

## Configuración
- Sistema operativo: Ubuntu Server 24.04 LTS
- Virtualización: Oracle VirtualBox
- Red: NAT
- Dirección IPv4 del servidor: `10.0.2.15`
- Servicio remoto: OpenSSH Server
- Puerto SSH del servidor: `22`
- Puerto anfitrión de VirtualBox: `2222`
- Dirección de conexión desde Windows: `127.0.0.1`

## Procedimiento
1. Revisar la interfaz de red y la dirección IP.
2. Instalar y habilitar OpenSSH Server.
3. Configurar el reenvío del puerto TCP 2222 al puerto 22.
4. Conectarse desde Windows mediante PowerShell.
5. Validar el funcionamiento de la sesión SSH.

## Resultado
Se estableció una sesión SSH desde Windows hacia Ubuntu Server correctamente.

## Aprendizajes
- Identificación de interfaces y direcciones IP.
- Administración de servicios mediante `systemctl`.
- Acceso remoto seguro mediante SSH.
- Reenvío de puertos en una máquina virtual con NAT.

## Evidencias pendientes
- Captura de la sesión SSH establecida.
- Resultado de `systemctl is-active ssh`.
- Resultado de `ip -br addr`.
