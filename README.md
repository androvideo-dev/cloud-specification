# cloud-specification


The device always connects to the cloud.  

## WebSocket Protocol
The data serialization/deserialization is [bson](http://bsonspec.org/).

### Connect to the server.
wss://api.cloud-domain.com/v1
```js
{
  headers: {
    'Device-Build-Version': 'V200_2018_03_20_643_Advan_debug',
    'Device-OS-Version': 'Android 5.1.1',
    'Device-Kernel-Version': '3.10.73-ga1a3c0c-00098-ged2cd52',
    'Device-HW-Version': 'EVT2',
    'Device-Mac-Address': '00-13-E2-FA-0C-1E',
    'Device-Serial-Number': '000017164994'
  }
}
```

### Send the request from the device.
```js
{
  type: 'request',
  id: 'random string',
  method: 'get',    // Follow http request method.
  uri: '/me?q=xx',  // Follow RESTful API path naming.
  body: {           // There is no body member when the method is get or delete.
    xx: '...'
  }
}
```

### Send the response to the device.
```js
{
  type: 'response',
  id: 'request id',
  status: 200,  // Follow http response status code.
  body: {
    xx: '...'
  }
}
```

### Broadcast to the device.
```js
{
  type: 'broadcast',
  event: 'ENROLL.RECORD.ADDED',
  body: {
    xx: '...'
  }
}
```
