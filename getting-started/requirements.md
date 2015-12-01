## Requirements

### Software

The Linkurious server can be deployed on the following platforms:
* Windows 7, 8, 8.1, and 10.
* Mac OS X Lion and more recent versions.
* Linux distributions such as Debian 6+, CentOS 6.5+, Ubuntu 12.10+, Gentoo, and Mint 14+.

End users will access Linkurious through a web browser. All modern browsers are supported:
* Chrome 23 or higher (fastest).
* Internet Explorer 10 or higher.
* Firefox 15 or higher.
* Safari 6 or higher.
* Opera 12 or higher.

The embedded ElasticSearch engine requires Java 8 to run properly.
**The JAVA_HOME environment variable must be set up**, see [how to do it on Windows here](http://docs.oracle.com/cd/E19182-01/820-7851/inst_cli_jdk_javahome_t/index.html).

#### SQLite and GLIBC 2.14

Linkurious uses an embedded SQLite database for persistence. This database requires GLIBC >= 2.14.
Some older Linux distributions don't have this version of GLIBC available. You can check the version available on your system on http://distrowatch.com .

If you encounter this problem, one solution is to use another persistence store for Linkurious, such as [MySQL](https://www.mysql.fr/) or [PostgreSQL](http://www.postgresql.org/).
You can use an existing database server or install a new one - Linkurious will store it's state in a specific "linkurious" database.
See the Configure section to change the persistence store used by Linkurious. Please refer to the official documentation of MySQL or PostgreSQL for installation and configuration of these databases.

Alternatively, on debian stable you may be able to fix the problem by upgrading GLIBC manually:

```Bash
echo 'deb http://ftp.fr.debian.org/debian/ testing main' > /etc/apt/sources.list
apt-get update
apt-get install -t testing libc6-dev=2.19-9
```

#### Data source

The Linkurious platform connects to remote data sources through HTTP or HTTPS. We currently support Neo4j servers version 2.0 and higher. Neo4j from Neo Technology is the leading graph database system on the market. You can calculate Neo4j's hardware requirements [here](http://neo4j.com/developer/guide-sizing-and-hardware-calculator/).

### Hardware

Hardware requirements of the platform depends on the size of the graph databases Linkurious is connected to. For up to 2 millions of nodes and relationships, we recommend to install the Linkurious server on a machine with 8 GB RAM, 4 CPU cores @ 2 Ghz, and 20 GB free disk space.

Hardware requirements of the Linkurious web client varies also with the size of the visualized graphs. For up to 500 nodes and edges, we recommend to use a machine with 4 GB RAM, and 2 CPU cores @ 1.6 Ghz. The minimal screen resolution is 1024x768 px.

