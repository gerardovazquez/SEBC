# kinit for the personal user principal

```sh
[root@ip-10-0-1-128 ~]# kinit gerardovazquez
Password for gerardovazquez@EXAMPLE.COM: 
[root@ip-10-0-1-128 ~]# klist -ef
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: gerardovazquez@EXAMPLE.COM

Valid starting     Expires            Service principal
03/09/17 09:10:31  03/10/17 09:10:29  krbtgt/EXAMPLE.COM@EXAMPLE.COM
	renew until 03/16/17 09:10:29, Flags: FRIA
	Etype (skey, tkt): aes256-cts-hmac-sha1-96, aes256-cts-hmac-sha1-96 
```

