# Github_OAuth
 how to build a "Sign in with Github" OAuth solution.
 
 # The web application flow to authorize users for your app is:

 1.Users are redirected to request their GitHub identity</br>
 2.Users are redirected back to your site by GitHub</br>
 3.Your app accesses the API with the user's access token</br>

# 1. Request a user's GitHub identity
GET https://github.com/login/oauth/authorize</br>
When your GitHub App specifies a login parameter, it prompts users with a specific account they can use for signing in and authorizing your app.</br>

# 2. Users are redirected back to your site by GitHub
If the user accepts your request, GitHub redirects back to your site with a temporary code in a code parameter as well as the state you provided in the previous step in a state parameter. The temporary code will expire after 10 minutes. If the states don't match, then a third party created the request, and you should abort the process.</br>

Exchange this code for an access token:</br>

POST https://github.com/login/oauth/access_token</br>

# 3. Use the access token to access the API
The access token allows you to make requests to the API on a behalf of a user.</br>

Authorization: token OAUTH-TOKEN</br>
GET https://api.github.com/user</br>
For example, in curl you can set the Authorization header like this:</br>

curl -H "Authorization: token OAUTH-TOKEN" https://api.github.com/user
