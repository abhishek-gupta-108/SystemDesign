
## Web Apis/Remote APis :
Phones have limited computational capacity. Remote Apis remove these constraints. Eg - Shazam, Google translate: Using the camera in real time sends the http request to the server and updates the image text.


### How Web Works?
+------------------+                             +------------------+
|      Client      |                             |      Server      |
|    (Browser)     |                             |   (Web Server)   |
+------------------+                             +------------------+
         |                                                   |
         | -------- HTTP GET /index.html (URI) ------------> |
         |                                                   |
         | <----------- HTML Response ---------------------- |
         |                                                   |
      https::\\google.com


Architectures :
## SOAP

## REST
An architecture style that is clear and allowed devs to iteract with resources over the web. <br>
When APis embrace the style and constrainst of REST, they are called RESTful.<br>
Generally, RESTful APIs return a Json response to the client<br>

Constrainsts:
1. Client Server Architecture
2. Statelessness   ==> HTTP is Stateless
3. Cachebility     ==> Read Wiki about HTTP. With headers you can provide some cachebility
4. Layered System
5. Code on Demand
6. Uniform Interface

Most of what we want our applications to do to the resources can be expressed as "CRUD"

| HTTP Verb | CRUD |
|------|------------|
| Get | Read |
| Post | Create |
| Put | Update |
| Patch |   |
| Delete | Delete |

Q) How to Get Response from an endpoint? - Curl , Postman

## GraphQL

## gRPC

## WebSocket

## WebHook

## MQTT

## AMQP
