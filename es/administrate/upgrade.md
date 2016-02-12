## Actualizar

<div class="alert alert-danger">
    Por favor haga una copia de seguridad de Linkurious antes de realizar cualquier actualización.
</div>

### Actualizaciones automáticas

Si usted tiene Linkurious v0.10.0 o más reciente instalado, usted puede actualizar utilizando el script de actualización automática:

1. Descargue la versión mas reciente de Linkurious desde nuestro sitio web (por ejemplo `linkurious-linux-v1.0.0.zip`) y guárdela en el directorio de Linkurious.
2. Pare Linkurious utilizando el script `stop`.
3. Haga una copia del directorio `data`. Si usted utiliza una base de datos externa para la persistencia (por ejemplo MySQL o PostgreSQL), haga una copia del esquema `linkurious` de la base de datos también.
4. Lance el script de actualización (Linux: `update.sh`, OSX: `update.sh.command`, Windows: `update.bat`).
5. Inicie Linkurious con normalidad.

### Actualizaciones manuales

Para versiones de Linkurious previas a v0.10, no hay un procedimiento de actualización disponible. Para actualizar Linkurious, usted necesita instalar una nueva versión y borrar la anterior. Todas las visualizaciones, usuarios, grupos y permisos de acceso se perderán.

En algunos casos, copiar el archivo `database.db` del directorio antiguo de Linkurious al nuevo directorio de Linkurious podría funcionar, pero no está garantizado y depende de las versiones.
