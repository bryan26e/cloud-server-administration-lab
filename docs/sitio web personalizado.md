# Despliegue de sitio web personalizado con Nginx

## 1. Descripción

En esta etapa del laboratorio `cloud-server-administration-lab` se realizó el despliegue de un sitio web personalizado en Ubuntu Server utilizando Nginx como servidor web.

El objetivo fue reemplazar la página web predeterminada o anterior por un sitio propio, permitiendo su acceso desde el equipo anfitrión Windows mediante VirtualBox.

## 2. Objetivos

- Publicar un sitio web personalizado en Ubuntu Server.
- Transferir archivos desde Windows hacia Linux.
- Utilizar Nginx para servir contenido web.
- Verificar el funcionamiento del servidor HTTP.
- Documentar el proceso como evidencia de administración de servidores Linux.

## 3. Entorno utilizado

| Componente | Configuración |
|---|---|
| Sistema operativo del servidor | Ubuntu Server |
| Servidor web | Nginx |
| Directorio de publicación | `/var/www/html` |
| Virtualización | VirtualBox |
| Red | NAT |
| Puerto interno | TCP 80 |
| Puerto externo | TCP 8080 |
| Acceso desde Windows | `http://127.0.0.1:8080` |

## 4. Procedimiento realizado

1. Se identificó la ubicación de los archivos del sitio web en Windows.
2. Se prepararon los archivos para transferirlos al servidor.
3. Se cargó el contenido del sitio web en Ubuntu Server.
4. Se publicó el nuevo contenido mediante el directorio web de Nginx.
5. Se accedió al sitio desde el navegador de Windows utilizando la redirección de puertos de VirtualBox.

## 5. Validación del servicio

Se utilizaron los siguientes comandos para comprobar el funcionamiento del servidor:

```bash
sudo nginx -t
systemctl is-active nginx
curl -I http://localhost
```

La validación permite comprobar la sintaxis de la configuración, el estado del servicio y la respuesta HTTP del servidor.

## 6. Acceso al sitio web

El sitio se encuentra disponible desde el equipo anfitrión mediante:

`http://127.0.0.1:8080`

VirtualBox redirige las conexiones del puerto 8080 del equipo anfitrión hacia el puerto 80 del servidor Ubuntu.

## 7. Evidencias

Las capturas de pantalla de esta actividad se almacenan en:

`evidence/05-servidor-web/`

- `06-sitio-personalizado.png`: sitio web publicado.
- `07-validacion-nginx.png`: validación de Nginx.
- `08-respuesta-http.png`: respuesta HTTP del servidor.

## Comandos ejecutados

## Copia de seguridad de los archivos del servidor ##
sudo cp -a /var/www/html "/var/www/html-backup-$(date +%F-%H%M)"
Comprobacion  ls -ld /var/www/html-backup-*

Comprimir pagina personalizada  
$Sitio = "$env:USERPROFILE\Documents\cloud-server-administration-lab\Portafolio\"
Test-Path "$Sitio\index.html" = como resultado debe ser True

Compress-Archive -Path "$Sitio\*" -DestinationPath "$env:USERPROFILE\Documents\cloud-server-administration-lab\Portafolio.zip" -Force

## Copiar archivos de windows a ubuntu
scp -P 2222 "$env:USERPROFILE\Documents\cloud-server-administration-lab\Portafolio.zip" cloud-server@127.0.0.1:/tmp/Portafolio.zip

Extraer
ls -lh /tmp/Portafolio.zip
mkdir -p /tmp/Portafolio
unzip -o /tmp/Portafolio.zip -d /tmp/Portafolio

Revisar contenido
find /tmp/Portafolio/ -maxdepth 3 -type f | head -n 30

Comprobar que el archivo principal esta en la ruta correcta
ls -l /tmp/Portafolio/index.html

Limpiar contenido anterior
sudo find /var/www/html -mindepth 1 -maxdepth 1 -exec rm -rf -- {} +

Copiar archivos nuevos
sudo cp -a /tmp/Portafolio/. /var/www/html/

Configurar permisos
sudo chown -R www-data:www-data /var/www/html
sudo find /var/www/html -type d -exec chmod 755 {} \;
sudo find /var/www/html -type f -exec chmod 644 {} \;

Validar Nginx
sudo nginx -t
sudo systemctl reload nginx
systemctl is-active nginx
curl -I http://localhost


## 8. Resultado

Se consiguió publicar un sitio web personalizado en Ubuntu Server utilizando Nginx y acceder a él desde Windows mediante la configuración NAT de VirtualBox.

## 9. Conclusión

Esta actividad permitió practicar un flujo básico de despliegue web en Linux, incluyendo la transferencia de archivos, publicación de contenido, administración de Nginx y comprobación de disponibilidad HTTP.

Estos conocimientos forman parte de las competencias fundamentales de administración de servidores, infraestructura Cloud y DevOps.