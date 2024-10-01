# CoreDNS Plugin DNS over HTTP(S)

A CoreDNS plugin that allows you to resolve DNS queries over HTTP(S).

This is based on the the [grpc plugin](https://github.com/coredns/coredns/tree/master/plugin/grpc)

## Syntax of Corefile

```corefile
. {
    doh FROM TO
}
```

where FROM is the base domain to match for the request to be proxied and TO is the destination endpoint to proxy to.

## Example

```corefile
. {
    doh . http://192.168.1.1:8053
}
```

When received the DNS query it will be proxied to http://192.168.1.1:8053/dns-query
Following a RFC 8484 request and response.