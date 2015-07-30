## Enable user authentication

<div class="alert alert-info">
  We strongly advise you to enable user authentication to secure the access to your data once Linkurious Enterprise is deployed on a server.
</div>

By default, user authentication is disabled. The unique user can do everything he wants and everybody can access the platform. First, we must create an administrator account.

<div class="alert alert-warning">
  If we don't create an administrator account before enabling authenticationw we will not be able to log in.
</div>

To do that, click on **Users** in the administrator dashboard, or selects the **Users** item in the **Admin** menu of the navigation bar. 

Once the user management dashboard is displayed, click on **Add** button next to "No Users". The user creation form appears.

![user-creation-form]](https://raw.githubusercontent.com/Linkurious/linkurious-enterprise-manual/master/screenshots/149.png)

Fill in all the fields and especially add the `admin` group in the groups field to grant administration rights to the new user. Once done click on **Save**.

We have created our first administrator. Now it is time to enable user authentication.

1. Open the linkurious folder in your computer.
- Open the file located at `linkurious/data/config/production.json` with your favorite text editor.
- Look for the `authRequired` key, then change its value from `false` to `true`.
- Restart Linkurious Enterprise.

User authentication is now enabled. Reload the user interface of the web application to display the login screen.

![login]](https://raw.githubusercontent.com/Linkurious/linkurious-enterprise-manual/master/screenshots/150.png)

Enter the login and password of the administrator to log in to Linkurious Enterprise.
