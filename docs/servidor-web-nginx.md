## Servidor web Nginx

## Objetivo
Instalar, configurar y verificar un servidor web en Ubuntu Server.

## Tecnologías
- Ubuntu Server 26.04.1 LTS
- Nginx
- SSH
- VirtualBox con red NAT

## Actividades realizadas
1. Instalación de Nginx mediante APT.
2. Habilitación del servicio para el inicio automático.
3. Verificación del estado con `systemctl`.
4. Acceso a la página desde Windows mediante el reenvío de puertos.
5. Publicación de una página HTML personalizada.
6. Inspección de los registros de acceso y errores.

## Comandos principales
- `systemctl is-active nginx`
- `sudo nginx -t`
- `sudo ss -tlnp | grep ':80'`
- `sudo tail -n 10 /var/log/nginx/access.log`
- `sudo tail -n 20 /var/log/nginx/error.log`

## Resultado
Servidor web operativo y accesible desde el navegador del equipo anfitrión.

## Evidencias
- Captura de la página web.
- Captura del estado de Nginx.
- Captura de la validación de configuración.
- Captura del registro de acceso.
