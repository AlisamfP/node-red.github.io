---
layout: default
title: Configuration
---
The following properties can be used to configure Node-RED.

When run as a standalone application, these properties are read from the `settings.js`
file. 

When [embedded](embedding.html), they are passed in the call to `RED.init()`.
However, when run in this mode, certain properties are ignored and are left to
the embedding application to implement.

### Editor Configuration

flowFile
: the file used to store the flows. Default: `flows_<hostname>.json`

userDir
: the directory to store all user data, such as flow and credential files and all
  library data. Default: the Node-RED install directory

nodesDir
: a directory to search for additional installed nodes. Node-RED searches the `nodes`
  directory under install directory. This property allows an additional directory
  to be searched, so that nodes can be installed outside of the Node-RED install
  structure.

uiHost
: the interface to listen for connections on. Default: 0.0.0.0 - 
  *all IPv4 interfaces*.

  *Standalone only*.

uiPort
: the port used to serve the editor UI. Default: 1880.
  
  *Standalone only*.

httpAdminRoot
: the root url for the editor UI. Default: '/'

httpAdminAuth
: enables HTTP Basic Authentication on the editor UI:

      httpAdminAuth: {user:"nol", pass:"5f4dcc3b5aa765d61d8327deb882cf99"}
  
  The `pass` property is the md5 hash of the actual password. The following
  command can be used to generate the hash:

      $ node -e "console.log(require('crypto').createHash('md5').update('YOUR PASSWORD HERE','utf8').digest('hex'))"
  
  *Standalone only*.

httpNodeRoot
: the root url for nodes that provide HTTP endpoints. Default: '/'

httpNodeAuth
: enables HTTP Basic Authentication. See `httpAdminAuth` for format.


https
: enables https, with the specified options object, as defined 
  [here](http://nodejs.org/api/https.html#https_https_createserver_options_requestlistener).

  *Standalone only*.

httpStatic
: a local directory from which to serve static web content from. This content is
  served from the top level url, '/'. When this property is used, `httpAdminRoot` must
  also be used to make editor UI available at a path other than '/'.

  *Standalone only*.

httpStaticAuth
: enabled HTTP Basic Authentication on the static content. See `httpAdminAuth` for format.

httpNodeCors
: enables cross-origin resource sharing for the nodes that provide HTTP endpoints,
  as defined [here](https://github.com/troygoode/node-cors#configuration-options)

### Node Configuration

Any node type can define its own settings to be provided in the file.

functionGlobalContext
: Function Nodes - a collection of objects to attach to the global function
  context. For example,

      functionGlobalContext: { os:require('os') }
  
  can be accessed in a function node as:
  
      context.global.os

debugMaxLength
: Debug Nodes - the maximum length, in characters, of any message sent to the
  debug sidebar tab. Default: 1000

mqttReconnectTime
: MQTT Nodes - if the connection is lost, how long to wait, in milliseconds, 
  before attempting to reconnect. Default: 5000

serialReconnectTime
: Serial Nodes - how long to wait, in milliseconds, before attempting to reopen
  a serial port. Default: 5000

socketReconnectTime
: TCP Nodes - how long to wait, in milliseconds, before attempting to reconnect.
  Default: 10000

socketTimeout
: TCP Nodes - how long to wait, in milliseconds, before timing out a socket.
  Default: 120000

