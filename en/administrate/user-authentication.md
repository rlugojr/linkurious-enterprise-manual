## Enable user authentication

<div class="alert alert-info">
  We strongly advise you to enable user authentication to secure the access to your data once Linkurious Enterprise is deployed on a server. This will allow you to enforce the limit of authenticated users with regards to your license terms.
</div>

By default, user authentication is disabled and all actions are performed under the special account named *"Unique User"*. The unique user can do everything he wants and is not required to log in, so everybody can access the platform. Before enabling user authentication we must create an administrator account.

<div class="alert alert-warning">
  If we don't create an administrator account before enabling authentication we will not be able to log in.
</div>

Let's create an administrator account. Click on **Users** in the administrator dashboard, or select the **Users** item in the **Admin** menu of the navigation bar. Once the user management dashboard is displayed, click on the **Add** button next to "No Users". The user creation form appears.

![user-creation-form](User-creation-form.png)

Fill in all the fields and especially add the `admin` group in the groups field to grant administration rights to the new user. Once done click on **Save**.

We have created our first administrator. Now it is time to enable user authentication.

1. Open the linkurious folder in your computer.
- Open the file located at `linkurious/data/config/production.json` with your favorite text editor.
- Look for the `authRequired` key, then change its value from `false` to `true`.
- Restart Linkurious Enterprise.

User authentication is now enabled. Reload the user interface of the web application to display the login screen.

![login](Login.png)

Enter the name (or email address) and password of the administrator to log in to Linkurious Enterprise.
