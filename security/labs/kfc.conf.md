# KDC config file

```ini
[kdcdefaults]
 kdc_ports = 88
 kdc_tcp_ports = 88

[realms]
EXAMPLE.COM = {
  acl_file = /var/kerberos/krb5kdc/kadm5.acl
  dict_file = /usr/share/dict/words
  admin_keytab = /var/kerberos/krb5kdc/kadm5.keytab
  supported_enctypes = aes256-cts:normal aes128-cts:normal des3-hmac-sha1:normal arcfour-hmac:normal des-hmac-sha1:normal des-cbc-md5:normal des-cbc-crc:normal
  default_principal_flags = +preauth +forwardable +proxiable +renewable
  max_renewable_life = 7d
  max_life = 24h
}
```