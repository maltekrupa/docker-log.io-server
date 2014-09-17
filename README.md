# Log.io-server Docker Container

## Contains
- log.io-server

You can find log.io-harvester in the corresponding repository [docker-log.io-harvester](https://github.com/temal-/docker-log.io-harvester).

## Example

```
docker run -d -p 28777:28777 -p 28778:28778 -v /path/to/config:/home/logio/.log.io --name logio-server temal/logio-server
```

### What you need to provide
#### Logserver configuration
Filename `log_server.conf` at `/path/to/config`.

Example:
```
exports.config = {
  host: '0.0.0.0',
  port: 28777
}
````

#### Webserver configuration
Filename `web_server.conf` at `/path/to/config`.

Example:
```
exports.config = {
  host: '0.0.0.0',
  port: 28778,

  /* 
  // Enable HTTP Basic Authentication
  auth: {
    user: "admin",
    pass: "1234"
  },
  */

  /* 
  // Enable HTTPS/SSL
  ssl: {
    key: '/path/to/privatekey.pem',
    cert: '/path/to/certificate.pem'
  },
  */

  /*
  // Restrict access to websocket (socket.io)
  // Uses socket.io 'origins' syntax
  restrictSocket: '*:*',
  */

  /*
  // Restrict access to http server (express)
  restrictHTTP: [
    "192.168.29.39",
    "10.0.*"
  ]
  */

}
```

### What to expect
Port 28777 is for receiving logs, 28778 is delivering the webinterface.

