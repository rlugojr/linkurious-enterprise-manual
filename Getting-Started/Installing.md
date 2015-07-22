## Install

Once you have downloaded a copy of Linkurious Enterprise, unzip the file into the folder you want.

### Install on Linux systems

It is recommended to deploy the Linkurious services with a restricted user account of the system. It may be dangerous to use the `root` account.

The Linkurious server is available by default on port 3000. However, most firewalls block network traffic of unusual ports and system users others than `root` cannot run processes that will use ports lower than the number 1024. To provide the service through the port 80, you may reroute traffic from 80 to 3000 as follows:

> sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 3000


### Install on MAC OS X

### Install on Windows

![picture of the download folder](https://dl.dropboxusercontent.com/s/1y73tkflooy9bi9/11.png?dl=0)

[Unzip](http://customize.org/help/How_To_Unzip_A_File) that file in the folder of your choice.

![linkurious enterprise folder](https://dl.dropboxusercontent.com/s/l06cj5kmlrku3ls/12.png?dl=0)

The installation is complete. If you want , you can remove the zip file.
