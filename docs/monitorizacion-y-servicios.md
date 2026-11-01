## Monitorización y registros

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
1. Resumen de monitorización de recursos
Indicador	Resultado	Interpretación
Tiempo activo	12 horas y 45 minutos	El servidor lleva más de medio día funcionando.
Usuarios conectados	2	Se registran dos sesiones de usuario.
Carga promedio (1, 5 y 15 min)	0.00, 0.00, 0.00	No existe carga significativa.
Memoria RAM total	2.5 GiB	Memoria asignada a la máquina virtual.
RAM utilizada	408 MiB	Consumo bajo de memoria.
RAM disponible	2.1 GiB	Existe suficiente memoria disponible.
Memoria Swap	0 B	No se ha configurado espacio de intercambio.
Almacenamiento total (/)	25 GB	Capacidad de la partición principal.
Almacenamiento utilizado	3.1 GB	Espacio ocupado por el sistema y sus archivos.
Almacenamiento disponible	21 GB	Espacio libre suficiente.
Uso del disco	14 %	Nivel de utilización bajo.

2. Análisis de CPU y procesos
Resultados obtenidos mediante top y ps aux --sort=-%mem.
Indicador	Resultado	Interpretación
Procesos y tareas	104	Total de tareas identificadas.
Procesos ejecutándose	1	Una tarea estaba ejecutándose al momento de la consulta.
Procesos durmiendo	103	La mayoría esperaba eventos o recursos.
Procesos detenidos	0	No había procesos detenidos.
Procesos zombie	0	No se identificaron procesos zombie.
CPU en uso por usuario	0.3 %	Actividad mínima.
CPU en uso por sistema	0.7 %	Actividad mínima del sistema.
CPU inactiva	98.7 %	La mayor parte de la CPU estaba disponible.
Espera de operaciones de disco	0.0 %	No se observó espera significativa de E/S.

Principales procesos identificados por consumo de RAM:
Proceso	Usuario	RAM aproximada	Función
fwupd	root	1.8 %	Administración de actualizaciones de firmware.
snapd	root	1.7 %	Administración de paquetes Snap.
unattended-upgrade-shutdown	root	1.2 %	Gestión de actualizaciones automáticas durante el apagado.
networkd-dispatcher	root	1.1 %	Gestión de eventos relacionados con la red.
systemd-journald	root	0.7 %	Recopilación de registros del sistema.
systemd	root	0.6 %	Administrador principal de servicios y procesos.

3. Análisis de registros del sistema
Registro consultado	Resultado observado	Interpretación
journalctl -b -n 30	Eventos de systemd, sudo, cron y servicios auxiliares.	El sistema registra correctamente las actividades y eventos de los servicios.
Sesiones de sudo	Apertura y cierre de sesiones administrativas.	Se puede rastrear el uso de privilegios administrativos.
sysstat-collect.service	Ejecuciones completadas correctamente.	El servicio de recopilación de estadísticas del sistema funciona.
fwupd-refresh.service	Finalización exitosa.	La actualización de metadatos de firmware terminó correctamente.
systemd-hostnamed.service	Inicio y desactivación exitosa.	El servicio de gestión del nombre del host responde correctamente.
cron	Ejecución de tareas horarias.	El programador de tareas está ejecutando trabajos programados.

4. Supervisión del servicio Nginx
Evento	Fecha	Resultado	Interpretación
Inicio de Nginx	29/10/2026	Started successfully	El servidor web inició correctamente.
Detención de Nginx	29/10/2026	Stopped successfully	El servicio pudo detenerse correctamente.
Inicio posterior	29/10/2026	Started successfully	Nginx volvió a iniciar sin errores registrados en esos eventos.
Solicitud HTTP /	31/10/2026	HTTP 304	El navegador tenía una versión en caché que no necesitaba actualizarse.
Solicitud /favicon.ico	31/10/2026	HTTP 200 y posteriormente 304	El navegador pudo solicitar el icono del sitio correctamente.

5. Evaluación general del servidor
Área evaluada	Estado	Observación
Rendimiento de CPU	Correcto	Uso mínimo y carga promedio de 0.00.
Memoria RAM	Correcto	2.1 GiB disponibles.
Almacenamiento	Correcto	Solo 14 % de utilización.
Gestión de procesos	Correcto	No se identificaron procesos zombie.
Registro de eventos	Correcto	Se registran eventos del sistema y sesiones administrativas.
Servicio Nginx	Correcto	Se observan inicios y solicitudes HTTP exitosas.
Memoria Swap	Sin configurar	No existe espacio de intercambio. No es necesariamente un problema en este entorno, pero conviene documentarlo.

## Conclusión de la monitorización

Durante la evaluación del servidor Ubuntu se comprobó que el sistema mantiene un consumo reducido de recursos y presenta un funcionamiento estable.

La memoria RAM asignada es de 2.5 GiB, con aproximadamente 2.1 GiB disponibles. El almacenamiento principal tiene una capacidad de 25 GB, de los cuales se encuentran utilizados 3.1 GB, equivalentes al 14 %.

La carga promedio del sistema fue de 0.00 durante los intervalos de 1, 5 y 15 minutos. Asimismo, el procesador presentó un 98.7 % de tiempo inactivo durante la medición, sin procesos zombie identificados.

La revisión de los registros mediante journalctl permitió observar eventos administrativos, ejecuciones programadas de cron y operaciones de servicios del sistema. También se verificaron los registros de Nginx, identificando solicitudes HTTP con respuestas 200 y 304.

En general, los resultados indican que el servidor se encuentra operativo y dispone de recursos suficientes para las actividades implementadas en este laboratorio.

**Observación:** el sistema no tiene memoria Swap configurada. Esta condición queda documentada como parte de la configuración actual del entorno.


