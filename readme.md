# .NET OAuth2 (Google) Behind a Rev. Proxy

Simple example showing the use of auth in ASP.NET Core using Google login from behind a reverse proxy, see [this example on proxies](https://learn.microsoft.com/en-us/aspnet/core/host-and-deploy/proxy-load-balancer?view=aspnetcore-7.0), and [this tutorial on Google login](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/social/google-logins?view=aspnetcore-7.0).


### To run

- Ensure you have a [Google Cloud Project](https://cloud.google.com/resource-manager/docs/creating-managing-projects).
- Create some [credentials](https://developers.google.com/identity/protocols/oauth2/web-server#creatingcred):
    - Set the redirect URL to `http://localhost:5001/signin-oidc`.
    - When created, store the client ID by opening a terminal at the project root and using `dotnet user-secrets set "Authentication:Google:ClientId" "[your-client-id]"`
    - Repeat the same for the client secret with `dotnet user-secrets set "Authentication:Google:ClientSecret" "[your-client-secret]"`
- Run with `dotnet run`.
- Setup your reverse proxy to port 5001, forwarding http to 5054, forwarding `X-Forwarded-For` and `X-Forwarded-Proto` headers.
- Navigate to `http://localhost:5001` and sign in to your account. 

