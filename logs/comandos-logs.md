Tabla de comandos para consultar logs en Ubuntu Server
1. Logs generales del sistema
Comando	Funcionalidad
sudo journalctl	Muestra todos los registros disponibles del sistema.
sudo journalctl -n 50	Muestra los últimos 50 registros.
sudo journalctl -f	Sigue los registros en tiempo real.
sudo journalctl --since today	Muestra registros desde el inicio del día.
sudo journalctl --since "24 hours ago"	Muestra registros de las últimas 24 horas.
sudo journalctl -p err	Muestra registros de nivel error o superior.
sudo journalctl -p err -n 20	Muestra los últimos 20 registros de error o superior.

2. Logs de SSH
Comando	Funcionalidad
sudo journalctl -u ssh	Consulta los registros del servicio SSH.
sudo journalctl -u ssh -n 50	Muestra los últimos 50 registros de SSH.
sudo journalctl -u ssh -f	Monitorea eventos SSH en tiempo real.
sudo journalctl -u ssh \| grep -i "failed"	Busca intentos fallidos de autenticación SSH.
sudo grep -i "failed" /var/log/auth.log	Busca fallos de autenticación en el archivo de seguridad, si existe.

3. Logs de Nginx
Comando	Funcionalidad
sudo tail -n 50 /var/log/nginx/error.log	Muestra los últimos 50 errores de Nginx.
sudo tail -n 50 /var/log/nginx/access.log	Muestra las últimas 50 solicitudes HTTP.
sudo tail -f /var/log/nginx/access.log	Monitorea solicitudes HTTP en tiempo real.
sudo tail -f /var/log/nginx/error.log	Monitorea errores de Nginx en tiempo real.

4. Logs de UFW (Firewall)
Comando	Funcionalidad
sudo journalctl -k \| grep UFW	Busca eventos del firewall en los registros del kernel.
sudo grep UFW /var/log/ufw.log	Consulta eventos registrados por UFW, si el archivo existe.
sudo tail -f /var/log/ufw.log	Monitorea eventos del firewall en tiempo real.

5. Logs de actualizaciones
Comando	Funcionalidad
sudo less /var/log/unattended-upgrades/unattended-upgrades.log	Consulta el historial de actualizaciones automáticas.
sudo tail -n 50 /var/log/unattended-upgrades/unattended-upgrades.log	Muestra los últimos 50 registros de actualizaciones automáticas.
sudo less /var/log/apt/history.log	Consulta el historial de instalaciones y actualizaciones de paquetes.

6. Comandos auxiliares para analizar logs
Comando	Funcionalidad
tail -n 20 archivo.log	Muestra las últimas 20 líneas de un archivo.
tail -f archivo.log	Sigue un archivo en tiempo real.
grep "error" archivo.log	Busca una palabra específica.
grep -i "error" archivo.log	Busca sin distinguir mayúsculas y minúsculas.
less archivo.log	Permite navegar por un archivo de registro.
cat archivo.log	Muestra el contenido completo de un archivo.
journalctl --since "1 hour ago"	Filtra registros de la última hora.
journalctl -p warning	Muestra advertencias y niveles de mayor prioridad.

7. Archivos de logs importantes
Ruta	Contenido
/var/log/syslog	Eventos generales del sistema, si está habilitado.
/var/log/auth.log	Eventos de autenticación y seguridad, si está habilitado.
/var/log/kern.log	Eventos del kernel, si está habilitado.
/var/log/nginx/access.log	Solicitudes recibidas por Nginx.
/var/log/nginx/error.log	Errores de Nginx.
/var/log/ufw.log	Eventos del firewall UFW, si está habilitado.
/var/log/apt/history.log	Historial de operaciones de APT.
/var/log/unattended-upgrades/	Registros de actualizaciones automáticas.


8. Tabla rápida: comandos que debes memorizar
Estos son los más útiles para trabajar como administrador de sistemas Linux.
Comando	Uso principal
journalctl -f	Monitoreo en tiempo real.
journalctl -u ssh	Diagnóstico de SSH.
journalctl -p err	Detección de errores.
journalctl --since today	Auditoría diaria.
tail -f archivo.log	Seguimiento de logs.
grep -i "failed" archivo.log	Detección de fallos.
less archivo.log	Lectura de registros extensos.
systemctl status nginx	Estado y registros recientes de Nginx.

9. Práctica recomendada para tu laboratorio
Puedes ejecutar estos comandos para generar y analizar eventos reales:
# 1. Consultar actividad SSH
sudo journalctl -u ssh -n 20

# 2. Consultar solicitudes web
sudo tail -n 20 /var/log/nginx/access.log

# 3. Consultar errores del sistema
sudo journalctl -p err -n 20

# 4. Consultar actividad del firewall
sudo journalctl -k | grep UFW

# 5. Consultar actualizaciones automáticas
sudo tail -n 20 /var/log/unattended-upgrades/unattended-upgrades.log