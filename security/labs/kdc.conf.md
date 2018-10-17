```
[kdcdefaults]
 kdc_ports = 88
 kdc_tcp_ports = 88

[realms]
  XPRUIMORAIS.SEBC.ES = {
  #master_key_type = aes256-cts
  max_renewable_life = 7d 0h 0m 0s
  max_life = 1d 0h 0m 0s
  acl_file = /var/kerberos/krb5kdc/kadm5.acl
  dict_file = /usr/share/dict/words
  admin_keytab = /var/kerberos/krb5kdc/kadm5.keytab
# note that aes256 is ONLY supported in Active Directory in a domain / forrest operating at a 2008 or greater functional level.
# aes256 requires that you download and deploy the JCE Policy files for your JDK release level to provide
# strong java encryption extension levels like AES256. Make sure to match based on the encryption configured within AD for
# cross realm auth, note that RC4 = arcfour when comparing windows and linux enctypes
  supported_enctypes = aes256-cts:normal aes128-cts:normal arcfour-hmac:normal
  default_principal_flags = +renewable, +forwardable
 }
```
