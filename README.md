# CoreDNS Plugin DNS over HTTP(S)

A CoreDNS plugin that allows you to resolve DNS queries over HTTP(S).

WARNING: this repo is WIP.
PLEASE STOP ME IF ANYTHING LIKE THIS ALREADY EXIST: I asked and it seems nothing like this exist yet. The closest I can found is `forward` with TLS support and `grpc` plugins, but please correct me if I am wrong: https://github.com/coredns/coredns/issues/6890


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

## TODO
- [ ] Add a simple resolve handler that always resolve to 0.0.0.0
- [ ] Dockerize an environment to test the plugin
- [ ] Saving it as a hello world example for CoreDNS plugins
- [ ] Make a query to an existing DoH Server and return the result, and resolve
- [ ] Create a proxy file to parse DoH Server and other configurations
- [ ] Add tests
- [ ] Add documentation
- [ ] Add a simple example of a Corefile to the repository
- [ ] Publish the plugin to the CoreDNS plugin site
