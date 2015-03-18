## Enable user authentication

By default, user authentication is disabled. The unique user can do everything he wants and everybody can access the platform.

>> We strongly advise you to enable user authentication to secure the access to your data.

First, We must create an administrator account.

>> If we don't create an administrator account before enabling authenticationw we will not be able to log in.

To do that, we click on ```Users``` in the administrator dashboard to enter the Users panel.

![opening the user management](https://dl.dropboxusercontent.com/s/sclu8e2gj8q4fk6/99.png?dl=0)

We click on ```New user``` on the right.

![the user creation screen](https://dl.dropboxusercontent.com/s/pk1o1dzuzebpnf3/100.png?dl=0)

Fill in all the fields of the user creation form, and especially remove the ```default``` group and add the ```admin``` group in the groups field to grant administration rights to the new user.

![creating a user](https://dl.dropboxusercontent.com/s/85w4sm4fkh86t8d/109.png?dl=0)

Once it is done, We click on ```Create```.

We have created our first administrator. Now it is time to enable user authentication.

We go to  ```\linkurious\config``` in our Linkurious Enterprise directory.

We open the ```production.json``` file. We look for ```auth_required```. We change its value from ```false``` to ```true```. We restart Linkurious Enterprise.

User authentication is now enabled. Reload the user interface to get the login screen.

![admin login](https://dl.dropboxusercontent.com/s/ymsb2l06egytrte/110.png?dl=0)

We enter the login and password of the administrator to access Linkurious Enterprise.
