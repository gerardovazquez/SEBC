# Upgrade Cloudera Manager 

* Report the latest available version of the API

```sh 
v15gerardovazquez@INV00710:~$ curl -i  GET -u 'gerardovazquez:cloudera' 'http://udera01:7180/api/version'
curl: (6) Could not resolve host: GET
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=1nhqlhzu5py2f1ojbedoczf0jb;Path=/;HttpOnly
Content-Type: application/json
Date: Wed, 08 Mar 2017 13:23:39 GMT
Content-Length: 3
Server: Jetty(6.1.26.cloudera.4)

v15
```

* Report the CM version 

```sh
gerardovazquez@INV00710:~$ curl -i -X GET -u 'gerardovazquez:cloudera' 'http://loudera01:7180/api/v15/cm/version'
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=hgk8otddcpuh68iltqjkcwjy;Path=/;HttpOnly
Content-Type: application/json
Date: Wed, 08 Mar 2017 13:30:22 GMT
Transfer-Encoding: chunked
Server: Jetty(6.1.26.cloudera.4)

{
  "version" : "5.10.0",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20170120-1038",
  "gitHash" : "aa0b5cd5eceaefe2f971c13ab657020d96bb842a",
  "snapshot" : false
}
```


* List all CM users
```sh
gerardovazquez@INV00710:~$ curl -i -X GET -u 'gerardovazquez:cloudera' 'http://cloudera01:7180/api/v15/users'
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=1jonhydxz94wgmxe3r9774gr6;Path=/;HttpOnly
Content-Type: application/json
Date: Wed, 08 Mar 2017 13:28:35 GMT
Transfer-Encoding: chunked
Server: Jetty(6.1.26.cloudera.4)

{
  "items" : [ {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ]
  }, {
    "name" : "gerardovazquez",
    "roles" : [ "ROLE_ADMIN" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  } ]
}
```

* Report the database server in use by CM

```sh
gerardovazquez@INV00710:~$ curl -i -X GET -u 'gerardovazquez:cloudera' 'http://loudera01:7180/api/v15/cm/scmDbInfo'
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=482ys0x8bjqd40kv8gs0zwzm;Path=/;HttpOnly
Content-Type: application/json
Date: Wed, 08 Mar 2017 13:33:42 GMT
Transfer-Encoding: chunked
Server: Jetty(6.1.26.cloudera.4)

{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}
```
