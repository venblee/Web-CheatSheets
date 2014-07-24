Troubleshooting 
===============

CORS & XHR Credential Flag
--------------------------
Problem :

```
XMLHttpRequest cannot load http://localhost/.../signalr/hubs/signalr/negotiate?clientProtocol=1.4&connectionData=%5B%5D&_=1406193817026. A wildcard '*' cannot be used in the 'Access-Control-Allow-Origin' header when the credentials flag is true. Origin 'http://localhost:9000' is therefore not allowed access. (index):1
```


Solution Client Side:
 
```
// withCredentials: false = false, solves the bloody CORS & with Credential issue
connection.start({ withCredentials: false }).done(function () {...}
```

Solution Server Side :

Allows CORS

web.config (standard IIS)
```
<system.webServer>
  <modules>
    <remove name="WebDAVModule" />
  </modules>
    <httpProtocol>
    <customHeaders>
      <clear />
      <add name="Access-Control-Allow-Origin" value="*" />
      <add name="Access-Control-Allow-Methods" value="GET, POST, PUT, DELETE, OPTIONS" />
      <add name="Access-Control-Allow-Headers" value="Authorization, Origin, X-Requested-With, Content-Type, Accept" />
    </customHeaders>
  </httpProtocol>
</system.webServer>
```

startup.cs (OWIN)
```
public void Configuration(IAppBuilder app)
{
  app.UseCors(CorsOptions.AllowAll);
}
```
