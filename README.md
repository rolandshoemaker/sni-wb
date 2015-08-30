# sni-wb

A simple SNI workbench server that powers `*.sni-wb.bracewel.net`. Each subdomain serves
either a valid or invalid SSL certificate from various CAs and using various key types
and sizes for testing purposes. These certificates are served using `SNI`, hence the name,
and as such may not work with various devices or languages that lack support for this TLS
extension.

## Subdomain format

```
{CA DN or 'invalid'}-{Issuer CN}-{Key type}-{Key size}.sni-wb.bracewel.net
```

e.g. `lets_encrypt-isrg_root_x1-rsa-2048.sni-wb.bracewel.net`

## Certificate information

Sending a `GET` request to `*.sni-wb.bracewel.net/json` will return a JSON object
containing various information about the certificate that this subdomain serves,
these endpoints will also respond to `HTTP` as well as `HTTPS` requests so that
information can still be easily retrieved about invalid certificates.

### Format

```
```
