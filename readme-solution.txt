
*** Visual Studio-solution that was created from a guide inside "Auth0 by Okta" (https://auth0.com/)
A ready .Net solution was downloaded and modified, partly as described below in "log of some changes".
Tested with GitHub and Facebook logins (Google gives some strange javascript-error)



*** Log of some changes:
2024-11-28-1: Tried login using the application, got the error below:
ArgumentException: IDX20108: The address specified '[PII of type 'System.String' is hidden. For more details, see https://aka.ms/IdentityModel/PII.]' is not valid as per HTTPS scheme. Please specify an https address for security reasons. If you want to test with http address, set the RequireHttps property on IDocumentRetriever to false. (Parameter 'address')

2024-11-28-2: Updated appsettings.json with ClientID and Domain, got the error below:
IOException: Received an unexpected EOF or 0 bytes from the transport stream.
System.Net.Security.SslStream.<FillHandshakeBufferAsync>g__InternalFillHandshakeBufferAsync|189_0<TIOAdapter>(TIOAdapter adap, ValueTask<int> task, int minSize)

HttpRequestException: The SSL connection could not be established, see inner exception.
System.Net.Http.ConnectHelper.EstablishSslConnectionAsync(SslClientAuthenticationOptions sslOptions, HttpRequestMessage request, bool async, Stream stream, CancellationToken cancellationToken)

IOException: IDX20804: Unable to retrieve document from: '[PII of type 'System.String' is hidden. For more details, see https://aka.ms/IdentityModel/PII.]'.
Microsoft.IdentityModel.Protocols.HttpDocumentRetriever.GetDocumentAsync(string address, CancellationToken cancel)

InvalidOperationException: IDX20803: Unable to obtain configuration from: 'https://XXXX.eu.auth0.com/.well-known/openid-configuration'. Will retry at '2024-11-28 09:30:27 +00:00'. Exception: 'System.IO.IOException: IDX20804: Unable to retrieve document from: '[PII of type 'System.String' is hidden. For more details, see https://aka.ms/IdentityModel/PII.]'.
---> System.Net.Http.HttpRequestException: The SSL connection could not be established, see inner exception.
---> System.IO.IOException: Received an unexpected EOF or 0 bytes from the transport stream.

2024-11-28-3: Tried again after completing a mail-verification that was missed, got a web-page with info below:
Callback URL mismatch.
The provided redirect_uri is not in the list of allowed callback URLs.
Please go to the Application Settings page and make sure you are sending a valid callback url from your application.

2024-11-28-4: Problem with callback was fixed by entering "https://localhost:44327/callback" as data
for "Allowed Callback URLs" in "https://manage.auth0.com/dashboard/eu/XXXX/applications".

2024-11-29-1: Added info-text to start page and link to show "Claims".
NuGet-update of "Auth0.AspNetCore.Authentication".

2024-11-29-2: Renamed solution and csproj from "SampleMvcApp" to "MVCCoreAuth0".
