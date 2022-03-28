# docker_network_test

## docker desktop 4.5.1 (74721)
```
$ docker-compose up -d
$ docker-compose exec nginx1 curl -vvv -I host.docker.internal:8081
*   Trying 192.168.65.2:8081...
* Connected to host.docker.internal (192.168.65.2) port 8081 (#0)
> HEAD / HTTP/1.1
> Host: host.docker.internal:8081
> User-Agent: curl/7.74.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
HTTP/1.1 200 OK
< Server: nginx/1.21.6
Server: nginx/1.21.6
< Date: Mon, 28 Mar 2022 14:44:57 GMT
Date: Mon, 28 Mar 2022 14:44:57 GMT
< Content-Type: text/html
Content-Type: text/html
< Content-Length: 615
Content-Length: 615
< Last-Modified: Tue, 25 Jan 2022 15:03:52 GMT
Last-Modified: Tue, 25 Jan 2022 15:03:52 GMT
< Connection: keep-alive
Connection: keep-alive
< ETag: "61f01158-267"
ETag: "61f01158-267"
< Accept-Ranges: bytes
Accept-Ranges: bytes

< 
* Connection #0 to host host.docker.internal left intact
$ docker-compose stop nginx2
$ docker-compose exec nginx1 curl -vvv -I host.docker.internal:8081
*   Trying 192.168.65.2:8081...
* connect to 192.168.65.2 port 8081 failed: Connection refused
* Failed to connect to host.docker.internal port 8081: Connection refused
* Closing connection 0
curl: (7) Failed to connect to host.docker.internal port 8081: Connection refused
```

## 4.6.1 (76265)
```
$ docker-compose up -d
$ docker-compose exec nginx1 curl -vvv -I host.docker.internal:8081
*   Trying 192.168.65.2:8081...
* Connected to host.docker.internal (192.168.65.2) port 8081 (#0)
> HEAD / HTTP/1.1
> Host: host.docker.internal:8081
> User-Agent: curl/7.74.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
HTTP/1.1 200 OK
< Server: nginx/1.21.6
Server: nginx/1.21.6
< Date: Mon, 28 Mar 2022 14:49:00 GMT
Date: Mon, 28 Mar 2022 14:49:00 GMT
< Content-Type: text/html
Content-Type: text/html
< Content-Length: 615
Content-Length: 615
< Last-Modified: Tue, 25 Jan 2022 15:03:52 GMT
Last-Modified: Tue, 25 Jan 2022 15:03:52 GMT
< Connection: keep-alive
Connection: keep-alive
< ETag: "61f01158-267"
ETag: "61f01158-267"
< Accept-Ranges: bytes
Accept-Ranges: bytes

< 
* Connection #0 to host host.docker.internal left intact
$ docker-compose stop nginx2
$ docker-compose exec nginx1 curl -vvv -I host.docker.internal:8081
*   Trying 192.168.65.2:8081...
* Connected to host.docker.internal (192.168.65.2) port 8081 (#0)
> HEAD / HTTP/1.1
> Host: host.docker.internal:8081
> User-Agent: curl/7.74.0
> Accept: */*
> 
^C
$ docker-compose exec nginx1 curl -vvv -m 10 -I host.docker.internal:8081
*   Trying 192.168.65.2:8081...
* Connected to host.docker.internal (192.168.65.2) port 8081 (#0)
> HEAD / HTTP/1.1
> Host: host.docker.internal:8081
> User-Agent: curl/7.74.0
> Accept: */*
> 
* Operation timed out after 10002 milliseconds with 0 bytes received
* Closing connection 0
curl: (28) Operation timed out after 10002 milliseconds with 0 bytes received
```
