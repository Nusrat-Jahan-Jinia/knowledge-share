# Why is Nginx called a reverse proxy?

## Contents

- [Proxy Types](#proxy-types)
  - [Forward Proxy](#forward-proxy)
  - [Purpose of forward proxy?](#purpose-of-forward-proxy)
  - [Reverse Proxy](#reverse-proxy)
  - [Anycast](#antcast)
  - [Performance](#performance)
  - [Benefits](#benefits)
  - [References](#references)

## Proxy Types
2 types of proxy. Forward proxy and reverse proxy.

![](./images/old-cdn.png)



## Forward Proxy?

A forward proxy is a server that sits between a group of client machines and the internet. When those clients make request to websites on the internet, the forward proxy acts as a middleman intercepts those requests and talks to web servers on behalf of those client machines.

## Purpose of forward proxy?
  1. A forward  proxy protects the client's online identity. By using a forward proxy to connect to a website, the IP address of the client is hidden from the server. Only the IP address of proxy is visible. It would be harder to trace back to the client.
  2. A forward proxy can be used to bypass browing restrictions. Some institutions like governments, schools, and big business use firewalls to restrict access to the internet. By connecting to a forward proxy outsite the firewalls, the client machine can potentailly get around these restrictions. It does not always work because the firewalls themeselves could block the connections to the proxy.
  3. A forward proxy can be used to block access to certain content. This is not uncommon for schools and business to configure their networks to connect all clients to the web though a proxy and apply filtering rules to disallow sites like social networks. For large institutions usually apply a technique called transparent proxy to streamline the process. A transparent proxy works with layer 4 switches to redirect certain types of traffic to the proxy automatically.


## Reverse Proxy
A reverse proxy sits between the internet and the web servers. It intercepts the request from clients and talk to the web server on hehalf of the clients.


## Purpose of reverse  proxy?

A reverse proxy could protect a website.

### Performance

1.Static contents are cached on the edge server in this content cache. If a piece of content is in the cache, it could be quickly retured to the user. Sice the edge server only asks for the copy of the static content from the origin server if it is not in it's content.

2. This greatly reduces the load and bandwidth requirements of the origin server cluster. A modern CDN could also transform static content into more optimized formats. It could minify js bundles on the fly, transform an image file from an old format to a modern one like WebP or AVIF.

3. The edge server also serves a very important role in the modern HTTP stack. All TLS connection terminates at the edge server. TLS hanshake are expensive. The commonly used TLS versions like TLS 1.2 take several network round trips to established. By terminating the TLS connection at the edge, it significantly reduces the latency for the user to establish an encrypted TCP connection. This is one reason why many modern applications send even dynamic uncachable HTTP content over the CDN.

### Benefits

# Security:

All modern CDNs have huge network capacity at the edge. This is the key to providing effective DDoS protection agaist large-scale attacks by having a network with a capacity much larger that the attackers. This is specially effective a CDN build on an anycast network. It allows the CDN to diffuse the attack traffic over a huge number of servers.

# Availability:

As they are ditributed, by having copies of content available in many PoPs, a CDN can withstand many more hardware failures than the original servers.

## References

https://www.youtube.com/watch?v=RI9np1LWzqw
