REST API

We can use Rest API’s to automate tableau server tasks.
Here I am taking usecase of creating and assign them to the tableau groups using Tableau API’s.

Discription:
Step1: need to sign in to the server, for that we need to use below Rest API to generate credentials token for particular site, this token will help to interact with the server.
Sign In
Signs you in as a user on the specified site on Tableau Server. This call returns a credentials token that you use in subsequent calls to the server. Typically, a credentials token is valid for 240 minutes. 
POST /api/api-version/auth/signin
Request Body
<tsRequest>
  <credentials name="username" password="password" >
    <site contentUrl="content-url" />
  </credentials>
</tsRequest>
Response Body:
<tsResponse>
  <credentials token="authentication-token" >
    <site id="site-id" contentUrl="content-url" />
    <user id="user-id-of-signed-in-user" />
  </credentials>
</tsResponse>

Add User to Site
Adds a user to Tableau Server and assigns the user to the specified site. If Tableau Server is configured to use local authentication, the information you specify is used to create a new user in Tableau Server.
POST /api/api-version/sites/site-id/users
Request Body
<tsRequest>
  <user name="user-name"
        siteRole="site-role"
        authSetting="auth-setting" />
</tsRequest>

Response Body
<tsResponse>
  <user id="user-id"
   name="user-name"
   siteRole="site-role"
   authSetting="auth-setting" />
</tsResponse>

Add User to Group
Adds a user to the specified group.
POST /api/api-version/sites/site-id/groups/group-id/users
Request Body

<tsRequest>
  <user id="user-id" />
</tsRequest>

Response Body
<tsResponse>
  <user id="user-id"
    name="user-name"
    siteRole="site-role" />
</tsResponse>

These API will login to the server as a admin and add user to the site with a site role and add him to specific group.
