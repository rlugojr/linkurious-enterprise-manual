## Requisitos

### Software

El servidor de Linkurious puede ser desplegado en las siguientes plataformas:
* Windows 7, 8, 8.1, 10 y Server 2012.
* Mac OS X Lion o más reciente.
* Distribuciones Linux como Debian 6+, CentOS 6.5+, Ubuntu 12.10+, Gentoo y Mint 14+.

Los usuarios finales accederán Linkurious mediante un navegador web. Todos los navegadores modernos están soportados:
* Chrome 23 o más reciente (el más rápido).
* Internet Explorer 10 o más reciente.
* Firefox 17 o más reciente.
* Safari 7.
* Opera 12 o más reciente.

El motor ElasticSearch integrado necesita Java 8 para funcionar correctamente.
**La variable de entorno JAVA_HOME debe estar configurada**, ver [cómo hacerlo en Windows aquí](http://docs.oracle.com/cd/E19182-01/820-7851/inst_cli_jdk_javahome_t/index.html).

#### SQLite y GLIBC 2.14

Linkurious utiliza una base de datos SQLite integrada para la persistencia de datos. Esta base de datos requiere GLIBC >= 2.14.
Algunas distribuciones antiguas de Linux no tienen esta versión de GLIBC disponible. Puede comprobar la versión disponible para su sistema en http://distrowatch.com.

Si tiene este problema, una solución es utilizar otra base de datos para Linkurious, como [MySQL](https://www.mysql.fr/) o [PostgreSQL](http://www.postgresql.org/).
Puede utilizar un servidor de base de datos existente o instalar uno nuevo. Linkurious almacenará su estado en una base de datos específica llamada "linkurious".
Consulte la sección de configuración para modificar la base de datos utilizada por Linkurious. Por favor compruebe la documentación oficial de MySQL o PostgreSQL para instalar y configurar estas bases de datos.

Alternativamente, en la versión Debian estable podría arreglar el problema actualizando GLIBC manualmente:

```Bash
echo 'deb http://ftp.fr.debian.org/debian/ testing main' > /etc/apt/sources.list
apt-get update
apt-get install -t testing libc6-dev=2.19-9
```

#### Fuente de datos

La plataforma Linkurious se conecta a fuentes de datos remotas mediante HTTP o HTTPS. Actualmente soportamos servidores Neo4j en la versión 2.0 o más actual. Neo4j, de Neo Technology, es la base de datos de grafos líder en el mercado. Puede ver los requisitos de hardware de Neo4j [aquí](http://neo4j.com/developer/guide-sizing-and-hardware-calculator/).

### Hardware

Los requisitos de hardware de la plataforma dependen del tamaño de las bases de datos de grafos a las Linkurious que esté conectado. Para hasta 2 millones de nodos y relaciones, recomendamos instalar el servidor de Linkurious en una máquina con 8 GB de RAM, CPU de 4 cores a 2 Ghz, y 20 GB de espacio libre en el disco.

Los requisitos hardware del cliente web de Linkurious también varían con el tamaño de los grafos visualizados. Para hasta 500 nodos y relaciones, recomendamos utilizar una máquina con 4 GB de RAM y una CPU de 2 cores a 1.6 Ghz. La resolución de pantalla mínima es 1024x768 px.

