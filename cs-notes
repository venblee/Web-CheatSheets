Web.Config
==========

Enable CORS on IIS
------------------

- remove all reference to WebDAV
- add specific headers


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

