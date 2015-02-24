# Activate the user authentication

By default, the user authentication is desactivated.

You must create an administrator account before activating it, otherwise you won't be able to log in.

To do that, click on ```Users``` in the administrator dashboard to enter the Users panel.

![opening the user management](https://dl.dropboxusercontent.com/s/sclu8e2gj8q4fk6/99.png?dl=0)

Click on ```New user``` on the right.

![the user creation screen](https://dl.dropboxusercontent.com/s/pk1o1dzuzebpnf3/100.png?dl=0)

Fill in all fields of the user creation form ; remove the ```default``` group and add the ```admin``` group in the groups field to grand administration rights to the new user.

![creating a user](https://dl.dropboxusercontent.com/s/85w4sm4fkh86t8d/109.png?dl=0)

Once done, click on ```Create```.

We have created our first administrator.

Time to activate the user authentication. Go to  ```\linkurious\config``` in your Linkurious Enterprise directory.

Open the ```production.json``` file. Look for ```auth_required```. Change its value from ```false``` to ```true```.

The next time you will start Linkurious Enterprise, you will see a login page. The user authentication is now activated.

![admin login](https://dl.dropboxusercontent.com/s/ymsb2l06egytrte/110.png?dl=0)

Enter your login and password to access Linkurious Enterprise.

If you want other people to access the application, you will need to create user accounts for them.
