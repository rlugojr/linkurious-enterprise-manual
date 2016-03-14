## Activar autenticación de usuarios

<div class="alert alert-info">
  Recomendamos encarecidamente que usted active la autenticación de usuarios para hacer seguro el acceso a sus datos una vez que Linkurious Enterprise sea desplegado en un servidor web. Esto le permitirá imponer el límite de usuarios autenticados de acuerdo a sus términos de licencias.
</div>

Por defecto, la autenticación de usuarios está desactivada y todas las acciones son realizadas con la cuenta de usuario especial llamada *"Unique User"* (usuario único). El usuario único puede hacer cualquier acción y no necesita identificarse, de forma que todo el mundo puede acceder a la plataforma. Antes de activar la autenticación de usuarios debemos crear una cuenta de administrador.

<div class="alert alert-warning">
  Si no creamos la cuenta de administrador antes de activar la autenticación de usuarios no podremos identificarnos.
</div>

Creemos la cuenta de administrador. Haga clic en **Users** (usuarios) en el panel de administración, o seleccione el elemento **Users** en el menú **Admin** de la barra de navegación. Una vez que el panel de gestión sea mostrado, haga clic en el botón **Add** junto a "No Users" (sin usuarios). El formulario de creación de usuarios aparecerá.

![user-creation-form](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/administrate/User-creation-form.png)

Rellene todos los campos y especialmente añada el grupo `admin` en el campo Groups para conceder los permisos de administración al nuevo usuario. Una vez haya terminado haga clic en **Save** (guardar).

Hemos creado nuestro primer administrador. Ahora es el momento de activar la autenticación de usuarios.

1. Abra el directorio de linkurious en su sistema.
- Abra el archivo `linkurious/data/config/production.json` con su editor de texto favorito.
- Busque la clave `authRequired`, luego cambie su valor de `false` a `true`.
- Reinicie Linkurious Enterprise.

Ahora la autenticación de usuarios está activada. Recargue la interfaz de la aplicación web para acceder a la pantalla de identificación.

![login](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/administrate/Login.png)

Introduzca el nombre (o email) y contraseña del administrador para acceder a Linkurious Enterprise.
