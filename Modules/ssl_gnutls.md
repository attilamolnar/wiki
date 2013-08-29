---
title: Modules &raquo; m_ssl_gnutls
layout: default
---

## Description	

Provides SSL support for clients and servers.

## Installation

Required packages:

Debian Squeeze:
`apt-get install libgnutls26 libgnutls-dev gnutls-bin pkg-config`

## Configuration Tags

```
<gnutls starttls="on"
  advertisedports=""
  dhbits="2048"
  hash="md5"
  priority="NORMAL"
  certfile="conf/cert.pem" # conf/ is your config path
  crlfile="conf/crl.pem"
  keyfile="conf/key.pem"
  cafile="conf/ca.pem"
  dhfile="conf/dhparams.pem"
>
```
               
##### gnutls

Attribute | Type | Description
--------- | ---- | -----------
starttls | bool | controls whether STARTTLS functionality is enabled (default) or not
advertisedports | string | the value of this setting overrides the default `SSL=IP:PORT` line displayed in the 005 (ISUPPORT) numeric
dhbits | int | number of bits 
hash | string | hash algorithm to use when checking signatures, possible values: "md5" and "sha1". Defaults to md5 for compatibility reasons, use sha1 whenever possible
priority | string | a priority string to determine the order for ciphers, hash functions etc. Defaults to "NORMAL", see Extra resources section for further description
certfile | string | the certificate (chain) that will be sent to clients and possibly other servers
keyfile | string | the private key for your certificate
cafile | string | a certificate authority 
crlfile | string | a certificate revocation list
dhfile | string | a file containing Diffie–Hellman parameters (or DH parameters, DH primes) TODO


Certificates should be in **PEM format**.

## Certificates

### Your server certificate

This certificate is sent to all connecting clients, and therefore it's necessary to have one in order to use this module.
Your server certificate is read from `certfile`, and its accompaning private key is read from `keyfile`.

(Note: `cafile` and `crlfile` have nothing to do with your server certificate, see the Client certificates section)

#### Using a self-signed certificate

A self-signed certificate is generated and installed for you if you answer yes when prompted by `configure`.
This works out of the box, no further configuration is necessary.

#### Using an existing certificate

To use an existing certificate first make sure it is in **PEM** format and check if the *certificate and the private key are in separate files*.
Your certificate (`certfile`) should look like this:

```
-----BEGIN CERTIFICATE-----
...
...
...
-----END CERTIFICATE-----
```

If it looks like

```
-----BEGIN CERTIFICATE-----
...
...
...
-----END CERTIFICATE-----
-----BEGIN RSA PRIVATE KEY-----
...
...
-----END RSA PRIVATE KEY-----
```

then you need to move the private key (including header and footer) into a second file (`keyfile`), a simple text editor can do the job just fine.
If it is unlike any of the above, then probably it's not in PEM format and you need to [convert it](TODO LINK HERE) first.

##### Certificate chains

If your certificate is signed by a CA, then `certfile` needs to contain all certificates in the verification chain. These extra certificates could be included in a separate file (called a CA bundle) provided by the CA.
To use them, simply concatenate them in 'certfile'. Your certificate (the one with the private key) should be on the top.

```
-----BEGIN CERTIFICATE-----
your certificate
...
...
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
another certificate
...
...
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
a third certificate
...
...
-----END CERTIFICATE-----
```

You can check the order using
`gnutls-cli irc.example.com -p 6697`

Note: InspIRCd will not complain if you don't supply the necessary certificates in the chain, but clients will because they won't be able to verify your certificate.

##### Converting from other formats

Converting from PKCS7/DER to PEM:

`openssl pkcs8 -nocrypt -inform DER -outform PEM -in input.key -out output.pem`

Converting from PKCS#12 to PEM:

`openssl pkcs12 -nodes -nocerts -in input.p12 -out output.pem`

### Client certificates

SSL provides the ability for both the client and the server to present a certificate for verification. In most cases, this is not used: only the server presents a certificate, and the client does not identify itself at all (or uses other means, such as a username/password).
InspIRCd will accept client certificates if your IRC client offers one during the SSL connection. The fingerprint of this client certificate is viewable with the /SSLINFO command, and can be used for NickServ authentication in place of the normal username/password. For information on how to create a client certificate and on how to set up common clients, look at [OFTC's page on CertFP setup](http://www.oftc.net/oftc/NickServ/CertFP).

You can also use a CA to validate client certificates - that is, the individual users' certificates that they use to connect to your server.
This can be used by connect blocks to match trusted certificates using `<connect requiressl="trusted">` (requires m_sslinfo).

This is what `ca.pem` and `crl.pem` are used for. You do not need them for anything else, and if you are not checking client certificates, *you can ignore their error messages*.

## Commands

STARTTLS
STARTTLS, while technically a command, is not used by users but by clients instead.
If enabled, it allows supporting clients to use SSL without having a dedicated SSL port.

## User Modes

This module does not implement any user modes.

## Channel Modes

This module does not implement any channel modes.

## Extended Bans

This module does not implement any extended bans.

## Notes

Unloading this module will automatically disconnect all users and servers that are connected via GnuTLS.

## Extra Resources

GnuTLS priority string documentation: http://www.gnutls.org/manual/html_node/Priority-Strings.html#Priority-Strings
GnuTLS documentation regarding STARTTLS: http://www.gnutls.org/manual/html_node/Upward-negotiation.html#Upward-negotiation
