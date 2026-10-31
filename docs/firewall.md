## Fase 7 — Configuración inicial del firewall

### Herramienta
UFW (Uncomplicated Firewall).

### Política aplicada
- Conexiones entrantes: DENY por defecto.
- Conexiones salientes: ALLOW por defecto.
- SSH: TCP 22 permitido.
- HTTP: TCP 80 permitido.

### Verificaciones
- Firewall activo.
- Servicio SSH operativo.
- Servicio Nginx operativo.
- Conectividad remota desde Windows verificada mediante NAT y reenvío de puertos.

### Aprendizaje
Se configuró un firewall básico para limitar las conexiones entrantes y permitir únicamente los servicios necesarios para el laboratorio.
