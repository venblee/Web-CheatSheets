Transport protocols
===================

Refs

http://blog.pusher.com/what-came-before-websockets/
http://caniuse.com/cors

Websockets [webSockets]
-----------------------

**Prerequisite**

IIS 8+
Latest version of any modern browser, IE10+
CORS : Cross Resource Sharing Enabled

***web.config***


```


  <system.webServer>

      <modules runAllManagedModulesForAllRequests="true">
      </modules>

  </system.webServer>
```


**IIS Setup**

1. "Turn Windows features on or off"
2. Internet Information Services
3. World Wide Web Services
4. Application Development Features
5. WebSocket Protocol (or the equivalent if you are on a server SKU).

ServerSourceEvent (SSE) [serverSentEvents]
------------------------------------------

**Prerequisite**

FF, Chrome, (anything but IE)


Forever Frame [foreverFrame]
----------------------------

Should be avoided ... cause more issues rather than solving them

**Prerequisite**

IE

longPolling [longPolling]
-------------------------

Only for last resort fallback



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
