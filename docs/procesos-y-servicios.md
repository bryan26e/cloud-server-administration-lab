# Práctica: Procesos y servicios de Linux

**Proyecto:** cloud-server-administration-lab  
**Fase:** Administración de procesos y servicios  
**Sistema:** Ubuntu Server 24.04 LTS

## 1. Objetivo

Aprender a consultar los procesos activos, observar el uso de recursos y verificar el estado de los servicios del sistema.

## 2. Comandos ejecutados

| Comando | Propósito |
|---|---|
| `uptime` | Consultar tiempo activo y carga del sistema |
| `ps aux --sort=-%mem \| head` | Identificar procesos con mayor consumo de memoria |
| `top` | Observar procesos y recursos en tiempo real |
| `systemctl --type=service --state=running` | Listar servicios activos |
| `systemctl status cron --no-pager` | Consultar el estado de cron |

## 3. Resultados obtenidos

[Completar después de ejecutar los comandos.]

## 4. Evidencias

- Captura de los procesos ordenados por memoria.
- Captura de los servicios activos.
- Captura del estado del servicio cron.

## 5. Aprendizajes

[Explicar qué diferencia existe entre un proceso y un servicio, y cómo se consultan.]

## 6. Conclusión

[Indicar qué se comprobó y qué queda pendiente.]