# apache2 Attributes<a name="attributes-recipes-apache"></a>

**Note**  
These attributes are available only on Linux stacks\.

The [apache2 attributes](https://github.com/aws/opsworks-cookbooks/blob/release-chef-11.10/apache2/attributes/apache.rb) specify the [Apache HTTP server](http://httpd.apache.org/) configuration\. For more information, see [Apache Core Features](http://httpd.apache.org/docs/current/mod/core.html)\. For more information on how to override built\-in attributes to specify custom values, see [Overriding Attributes](workingcookbook-attributes.md)\.


****  

|  |  |  | 
| --- |--- |--- |
| [binary ](#attributes-recipes-apache-bin) | [contact ](#attributes-recipes-apache-contact) | [deflate\_types](#attributes-recipes-apache-deflate) | 
| [dir ](#attributes-recipes-apache-dir) | [document\_root ](#attributes-recipes-apache-doc-root) | [group ](#attributes-recipes-apache-group) | 
| [hide\_info\_headers ](#attributes-recipes-apache-hide) | [icondir ](#attributes-recipes-apache-icondir) | [init\_script ](#attributes-recipes-apache-init-script) | 
| [keepalive ](#attributes-recipes-apache-keep) | [keepaliverequests ](#attributes-recipes-apache-keep-requests) | [keepalivetimeout ](#attributes-recipes-apache-keep-timeout) | 
| [lib\_dir ](#attributes-recipes-apache-lib-dir) | [libexecdir ](#attributes-recipes-apache-libexecdir) | [listen\_ports ](#attributes-recipes-apache-ports) | 
| [log\_dir ](#attributes-recipes-apache-log-dir) | [logrotate Attributes](#attributes-recipes-apache-log) | [pid\_file ](#attributes-recipes-apache-pidfile) | 
| [prefork Attributes](#attributes-recipes-apache-prefork) | [serversignature ](#attributes-recipes-apache-sig) | [servertokens ](#attributes-recipes-apache-tokens) | 
| [timeout ](#attributes-recipes-apache-timeout) | [traceenable ](#attributes-recipes-apache-trace) | [user ](#attributes-recipes-apache-user) | 
| [version](#attributes-recipes-apache-version) | [worker Attributes](#attributes-recipes-apache-worker) |  | 

**binary **  
The location of the Apache binary \(string\)\. The default value is `'/usr/sbin/httpd'`\.  

```
node[:apache][:binary]
```

**contact **  
An e\-mail contact \(string\)\. The default value is a dummy address, `'ops@example.com'`\.  

```
node[:apache][:contact]
```

**deflate\_types**  
Directs `mod_deflate` to enable compression for the specified Mime types, if they are supported by the browser \(list of string\)\. The default value is as follows:  

```
['application/javascript',
 'application/json',
 'application/x-javascript',
 'application/xhtml+xml',
 'application/xml',
 'application/xml+rss',
 'text/css',
 'text/html',
 'text/javascript',
 'text/plain',
 'text/xml']
```
Compression can introduce security risks\. To completely disable compression, set this attribute as follows:  

```
node[:apache][:deflate_types] = []
```

```
node[:apache][:deflate_types]
```

**dir **  
The server's root directory \(string\)\. The default values are as follows:  

+ Amazon Linux and Red Hat Enterprise Linux \(RHEL\): `'/etc/httpd'`

+ Ubuntu: `'/etc/apache2'`

```
node[:apache][:dir]
```

**document\_root **  
The document root \(string\)\. The default values are as follows:  

+ Amazon Linux and RHEL: `'/var/www/html'`

+ Ubuntu: `'/var/www'`

```
node[:apache][:document_root]
```

**group **  
The group name \(string\)\. The default values are as follows:  

+ Amazon Linux and RHEL: `'apache'`

+ Ubuntu: `'www-data'`

```
node[:apache][:group]
```

**hide\_info\_headers **  
Whether to omit version and module information from HTTP headers \(`'true'`/`'false'`\) \(string\)\. The default value is `'true'`\.  

```
node[:apache][:hide_info_headers]
```

**icondir **  
The icon directory \(string\)\. The defaults value are as follows:  

+ Amazon Linux and RHEL: `'/var/www/icons/'`

+ Ubuntu: `'/usr/share/apache2/icons'`

```
node[:apache][:icondir]
```

**init\_script **  
The initialization script \(string\)\. The default values are as follows:  

+ Amazon Linux and RHEL: `'/etc/init.d/httpd'`

+ Ubuntu: `'/etc/init.d/apache2'`

```
node[:apache][:init_script]
```

**keepalive **  
Whether to enable keep\-alive connections \(string\)\. The possible values are `'On'` and `'Off'` \(string\)\. The default value is `'Off'`\.  

```
node[:apache][:keepalive]
```

**keepaliverequests **  
The maximum number of keep\-alive requests that Apache will handle at the same time \(number\)\. The default value is `100`\.  

```
node[:apache][:keepaliverequests]
```

**keepalivetimeout **  
The time that Apache waits for a request before closing the connection \(number\)\. The default value is `3`\.  

```
node[:apache][:keepalivetimeout]
```

**lib\_dir **  
The directory that contains the object code libraries \(string\)\. The default values are as follows:  

+ Amazon Linux \(x86\): `'/usr/lib/httpd'`

+ Amazon Linux \(x64\) and RHEL: `'/usr/lib64/httpd'`

+ Ubuntu: `'/usr/lib/apache2'`

```
node[:apache][:lib_dir]
```

**libexecdir **  
The directory that contains the program executables \(string\)\. The default values are as follows:  

+ Amazon Linux \(x86\): `'/usr/lib/httpd/modules'`

+ Amazon Linux \(x64\) and RHEL: `'/usr/lib64/httpd/modules'`

+ Ubuntu: `'/usr/lib/apache2/modules'`

```
node[:apache][:libexecdir]
```

**listen\_ports **  
A list of ports that the server listens to \(list of string\)\. The default value is `[ '80','443' ]`\.  

```
node[:apache][:listen_ports]
```

**log\_dir **  
The log directory \(string\)\. The default values are as follows:  

+ Amazon Linux and RHEL: `'/var/log/httpd'`

+ Ubuntu: `'/var/log/apache2'`

```
node[:apache][:log_dir]
```

**logrotate Attributes**  
These attributes specify how to rotate the log files\.    
**delaycompress **  
Whether to delay compressing a closed log file until the start of the next rotation cycle \(`'true'`/`'false'`\) \(string\)\. The default value is `'true'`\.  

```
node[:apache][:logrotate][:delaycompress]
```  
**group **  
The log files' group \(string\)\. The default value is `'adm'`\.  

```
node[:apache][:logrotate][:group]
```  
**mode **  
The log files' mode \(string\)\. The default value is `'640'`\.  

```
node[:apache][:logrotate][:mode]
```  
**owner **  
The log files' owner \(string\)\. The default value is `'root'`\.  

```
node[:apache][:logrotate][:owner]
```  
**rotate **  
The number of rotation cycles before a closed log file is removed \(string\)\. The default value is `'30'`\.  

```
node[:apache][:logrotate][:rotate]
```  
**schedule **  
The rotation schedule \(string\)\. Possible values are as follows:  

+ `'daily'`

+ `'weekly'`

+ `'monthly'`
The default value is `'daily'`\.  

```
node[:apache][:logrotate][:schedule]
```

**pid\_file **  
The file that contains the daemon's process ID \(string\)\. The default values are as follows:  

+ Amazon Linux and RHEL: `'/var/run/httpd/httpd.pid'`

+ Ubuntu: `'/var/run/apache2.pid'`

```
node[:apache][:pid_file]
```

**prefork Attributes**  
These attributes specify the pre\-forking configuration\.    
**maxclients **  
The maximum number of simultaneous requests that will be served \(number\)\. The default value is `400`\.  
Use this attribute only for instances that are running Amazon Linux, RHEL, or Ubuntu 12\.04 LTS\. If your instances are running Ubuntu 14\.04 LTS, use [maxrequestworkers](#attributes-recipes-apache-prefork-maxrequestworkers)\.

```
node[:apache][:prefork][:maxclients]
```  
**maxrequestsperchild **  
The maximum number of requests that a child server process will handle \(number\)\. The default value is `10000`\.  

```
node[:apache][:prefork][:maxrequestsperchild]
```  
**maxrequestworkers**  
The maximum number of simultaneous requests that will be served \(number\)\. The default value is `400`\.  
Use this attribute only for instances that are running Ubuntu 14\.04 LTS\. If your instances are running Amazon Linux, RHEL, or Ubuntu 12\.04 LTS, use [maxclients ](#attributes-recipes-apache-prefork-maxclients)\.

```
node[:apache][:prefork][:maxrequestworkers]
```  
**maxspareservers **  
The maximum number of idle child server processes \(number\)\. The default value is `32`\.  

```
node[:apache][:prefork][:maxspareservers]
```  
**minspareservers **  
The minimum number of idle child server processes \(number\)\. The default value is `16`\.  

```
node[:apache][:prefork][:minspareservers]
```  
**serverlimit **  
The maximum number of processes that can be configured \(number\)\. The default value is `400`\.  

```
node[:apache][:prefork][:serverlimit]
```  
**startservers **  
The number of child server processes to be created at startup \(number\)\. The default value is `16`\.  

```
node[:apache][:prefork][:startservers]
```

**serversignature **  
Specifies whether and how to configure a trailing footer for server\-generated documents \(string\)\. The possible values are `'On'`, `'Off'`, and `'Email'`\)\. The default value is `'Off'`\.  

```
node[:apache][:serversignature]
```

**servertokens **  
Specifies what type of server version information is included in the response header \(string\):  

+ `'Full'`: Full information\. For example, Server: Apache/2\.4\.2 \(Unix\) PHP/4\.2\.2 MyMod/1\.2 

+ `'Prod'`: Product name\. For example, Server: Apache

+ `'Major'`: Major version\. For example, Server: Apache/2

+ `'Minor'`: Major and minor version\. For example, Server: Apache/2\.4

+ `'Min'`: Minimal version\. For example, Server: Apache/2\.4\.2

+ `'OS'`: Version with operating system\. For example, Server: Apache/2\.4\.2 \(Unix\) 
The default value is `'Prod'`\.  

```
node[:apache][:servertokens]
```

**timeout **  
The amount of time that Apache waits for I/O \(number\)\. The default value is `120`\.  

```
node[:apache][:timeout]
```

**traceenable **  
Whether to enable `TRACE` requests \(string\)\. The possible values are `'On'` and `'Off'`\. The default value is `'Off'`\.  

```
node[:apache][:traceenable]
```

**user **  
The user name \(string\)\. The default values are as follows:  

+ Amazon Linux and RHEL: `'apache'`

+ Ubuntu: `'www-data'`

```
node[:apache][:user]
```

**version**  
The Apache version \(string\)\. The default values are as follows:  

+ Amazon Linux: `2.2`

+ Ubuntu 12\.04 LTS: `2.2`

+ Ubuntu 14\.04 LTS: `2.4`

+ RHEL: `2.4`

```
node[:apache][:version]
```

**worker Attributes**  
These attributes specify the worker process configuration\.    
**startservers **  
The number of child server processes to be created at startup \(number\)\. The default value is `4`\.  

```
node[:apache][:worker][:startservers]
```  
**maxclients **  
The maximum number of simultaneous requests that will be served \(number\)\. The default value is `1024`\.  

```
node[:apache][:worker][:maxclients]
```  
**maxsparethreads **  
The maximum number of idle threads \(number\)\. The default value is `192`\.  

```
node[:apache][:worker][:maxsparethreads]
```  
**minsparethreads **  
The minimum number of idle threads \(number\)\. The default value is `64`\.  

```
node[:apache][:worker][:minsparethreads]
```  
**threadsperchild **  
The number of threads per child process \(number\)\. The default value is `64`\.  

```
node[:apache][:worker][:threadsperchild]
```  
**maxrequestsperchild **  
The maximum number of requests that a child server process will handle \(number\)\. The default value is `10000`\.  

```
node[:apache][:worker][:maxrequestsperchild]
```