```
[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log

[libdefaults]
 default_realm = XPRUIMORAIS.SEBC.ES
 dns_lookup_realm = false
 dns_lookup_kdc = false
 ticket_lifetime = 24h
 renew_lifetime = 7d
 forwardable = true
# udp_preference_limit = 1

# set udp_preference_limit = 1 when TCP only should be
# used. Consider using in complex network environments when
# troubleshooting or when dealing with inconsistent
# client behavior or GSS (63) messages.

# uncomment the following if AD cross realm auth is ONLY providing DES encrypted tickets
# allow-weak-crypto = true

[realms]
 XPRUIMORAIS.SEBC.ES = {
  kdc = node01.xpandit.com:88
  admin_server = node01.xpandit.com:749
 }

# The domain_realm is critical for mapping your host domain names to the kerberos realms
# that are servicing them. Make sure the lowercase left hand portion indicates any domains or subdomains
# that will be related to the kerberos REALM on the right hand side of the expression. REALMs will
# always be UPPERCASE. For example, if your actual DNS domain was test.com but your kerberos REALM is
# EXAMPLE.COM then you would have,

[domain_realm]
.xpandit.com = XPRUIMORAIS.SEBC.ES
xpandit.com = XPRUIMORAIS.SEBC.ES
```
