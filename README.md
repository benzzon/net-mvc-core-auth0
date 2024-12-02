# net-mvc-core-auth0
.Net MVC Core application for testing with "playground" on auth0.


Steps for using/testing:

1. Get a free auth0-account at https://manage.auth0.com/
 Choose custom-config and select EU and set your own custom domain-name.
 Something like "myname.eu.auth0.com"

2. Create an "auth0-application" and copy the "Client ID".

3. Configure "Allowed Callback URLs" to "https://localhost:44327/callback", and "Allowed Logout URLs" to "https://localhost:44327/".
 (choose social-accounts to use for testing, like "GitHub" and "Facebook".)

4. Edit "appsettings.json" and update the keys "Domain" and "Client ID".

5. Run the solution and try the "login-link", followed by the link to show "Claims"
 
