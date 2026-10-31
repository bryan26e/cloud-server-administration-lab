# Fase 6: Monitorización y registros

## Objetivo
Aprender a supervisar los recursos del servidor y analizar eventos para detectar posibles problemas.

## Comandos practicados
- `uptime`: tiempo activo y carga del sistema.
- `free -h`: uso de memoria.
- `df -h`: espacio en disco.
- `ps aux --sort=-%mem | head -n 10`: procesos con mayor consumo de memoria.
- `top`: monitorización en tiempo real.
- `sudo journalctl -b -n 30 --no-pager`: eventos recientes del sistema.
- `sudo journalctl -u nginx -n 20 --no-pager`: eventos del servicio Nginx.
- `sudo tail -n 10 /var/log/nginx/access.log`: solicitudes HTTP.

## Resultados
Completar con los valores observados de memoria, disco, carga del sistema y registros de Nginx.

## Evidencias
- Captura del uso de memoria.
- Captura del espacio en disco.
- Captura de los eventos del sistema.
- Captura del registro de acceso web.
