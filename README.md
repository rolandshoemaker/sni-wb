# sni-wb

A simple SNI workbench server that powers `*.sni-wb.bracewel.net`. Each subdomain serves
either a valid or invalid SSL certificate from various CAs and using various key types
and sizes for testing purposes. These certificates are served using `SNI`, hence the name,
and as such may not work with various devices or languages that lack support for this TLS
extension.

## Subdomain format

```
{CA DN or 'invalid'}-{Issuer CN}-{Key type}-{Key size}-{Optional comment}.sni-wb.bracewel.net
```

Examples

```
lets_encrypt-isrg_root_x1-rsa-2048.sni-wb.bracewel.net
lets_encrypt-isrg_root_x1-rsa-2048-short_chain.sni-wb.bracewel.net
lets_encrypt-isrg_root_x1-rsa-2048-large_san.sni-wb.bracewel.net
lets_encrypt-isrg_root_x1-ecc-512.sni-wb.bracewel.net
```

## Directory

`HTTP` requests to `http://directory.sni-wb.bracewel.net` will return a JSON object
describing all currently served certificate subdomains. Various basic query parameters
can be passed in order to filter the returned results.

### Format

The directory takes the format of the a list of objects containing the certificate URI,
description URI, CA name, issuer name, key type, and key size. 

```
[
  {
    "certificateURI": "https://lets_encrypt-isrg_root_x1-rsa-2048.sni-wb.bracewel.net",
    "descriptionURI": "http://lets_encrypt-isrg_root_x1-rsa-2048.sni-wb.bracewel.net/json",
    "ca": "Let's Encrypt",
    "issuer": "ISRG Root X1",
    "keyType": "RSA",
    "keySize": 2048
  },
  {
    "certificateURI": "https://lets_encrypt-isrg_root_x1-rsa-2048-short_chain.sni-wb.bracewel.net",
    "descriptionURI": "http://lets_encrypt-isrg_root_x1-rsa-2048-short_chain.sni-wb.bracewel.net/json"
    "ca": "Let's Encrypt",
    "issuer": "ISRG Root X1",
    "keyType": "RSA",
    "keySize": 2048
  }
]
```

## Certificate information

Sending a `GET` request to `http://*.sni-wb.bracewel.net/json` will return a JSON object
containing various information about the certificate that this subdomain serves,
these endpoints will also respond to `HTTP` requests so that information can still be
easily retrieved about invalid certificates.

### Format

```
```
