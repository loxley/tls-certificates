# tls-certificates

This is a demo application to support this blog post. It demonstrates how to apply mTLS configuration on client and the server in Go.

## project structure
```bash
.
├── 00-certificates           # holds all the certificates used for demonstration
│   ├── client                # client certificate and private key
│   │   ├── cert.pem
│   │   └── key.pem
│   ├── minica-key.pem        # self-signed root certificate  
│   ├── minica.pem            # private key for root certificate
│   └── server                # server certificate and private key
│       ├── cert.pem
│       └── key.pem
├── 01-http-server            # simple http server
│   └── client
├── 02-https-server           # secured server
│   └── server
└── 03-https-server-mtls      # secured server and client
    └── server
```
## certificates generated using minica

find more details about using minica [here](https://github.com/jsha/minica)

## generating certificates

generate certificates for testing using below commands:
```bash
minica --domains server-cert    # this will generate certificate for a domain "server-cert"
minica --domains client-cert    # this will generate certificate for a domain "client-cert"
```

## further configuration on your local machine

add below hostnames to your local machine. For example on linux, update the `/etc/hosts` file with below entries.
```bash
127.0.0.1       server-cert
127.0.0.1       client-cert
```
this will create an alias for loopback address. 