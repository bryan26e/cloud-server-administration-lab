# Práctica: Administración de servidores Linux en la nube

**Proyecto:** cloud-server-administration-lab  
**Fase:** 1.0  
**Fecha:** 29-10-2026  
**Estado:** En progreso

# Cloud Server Administration Lab

## Descripción

Laboratorio práctico de administración de servidores Linux, enfocado en infraestructura cloud, seguridad de servidores y operaciones DevOps.

El proyecto utiliza Ubuntu Server ejecutado en Oracle VirtualBox para implementar, configurar, administrar y proteger un entorno de servidor.

## Objetivos

- Administrar usuarios, grupos y permisos en Linux.
- Configurar servicios SSH y Nginx.
- Implementar reglas de seguridad mediante UFW.
- Gestionar procesos y servicios del sistema.
- Supervisar recursos y analizar registros.
- Aplicar medidas de endurecimiento de seguridad.
- Documentar procedimientos y evidencias técnicas.

## Tecnologías utilizadas

| Tecnología | Uso |
|---|---|
| Ubuntu Server | Sistema operativo |
| Oracle VirtualBox | Virtualización |
| OpenSSH | Administración remota |
| Nginx | Servidor web |
| UFW | Firewall |
| Chrony | Sincronización horaria |
| systemd | Gestión de servicios |
| Git y GitHub | Control de versiones y documentación |

## Seguridad implementada

- Acceso SSH mediante claves Ed25519.
- Acceso SSH de root deshabilitado.
- Autenticación SSH por contraseña deshabilitada.
- Firewall UFW activo.
- Política predeterminada de entrada denegada.
- Revisión de usuarios y privilegios sudo.
- Auditoría de puertos y servicios.
- Actualizaciones automáticas de seguridad habilitadas.

## Estructura del repositorio

- `docs/`: documentación técnica.
- `evidence/`: capturas de pantalla y resultados de pruebas.
- `logs/`: bitácora de actividades y cambios.

## Estado del proyecto

Laboratorio local implementado y en fase de documentación técnica.

## Autor

Bryan Daniel Mendez Barrios

Proyecto personal de aprendizaje y desarrollo de habilidades en Linux Administration, Cloud Security y DevOps.