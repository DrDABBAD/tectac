---
title: When to use a reverse proxy with the ASP.NET Core Kestrel web server
date: 2017-09-12 00:00:00 +0300
description: When to use a reverse proxy in front of Kestrel, the cross-platform web server for ASP.NET Core.
img: ./software.jpg # Add image post (optional)
tags:  [appsettings.json, "ASP.NET Core Identity", cookie, Cookie, Blazor, "Blazor Server", "Blazor WebAssembly", "Identity", "Let's Encrypt", Razor, SignalR]
---

# What is Kestrel

A Kestrel Web server in written in ASP.NET core is not meant to act as an application server or Edge Server that handles very specific data processing tasks. Kestrel is optimized for application scenarios, but it's not optimized for other things like static file serving or managing the server's lifetime.


## What is reverse proxy

A reverse proxy is a server that *sits in front of web servers* and forwards client  HTTP requests (e.g. generally web browser) requests to those web servers.
Reverse proxies are typically implemented to help increase security, performance, and reliability. This is achived through SSL encryption , DDOS attack protection ,load balancing and caching.

## So what is a proxy server

proxy server, or web proxy, is a server that *sits in front of a group of client machines*. When those computers make requests to sites and services on the Internet, the proxy server intercepts those requests and then communicates with web servers on behalf of those clients, like a middleman. The main use of forwzard proxy are content filter; to avoid  institualtional browser restrictions  protect identity.



When to use Kestrel with a reverse proxy

Kestrel can be used by itself or with a *reverse proxy server*, such as [Internet Information Services (IIS)](https://www.iis.net/), [Nginx](https://nginx.org), or [Apache](https://httpd.apache.org/).

When Kestrel is used as an edge server (Internet-facing)  without a reverse proxy server, sharing of the same IP address and port among multiple processes is unsupported. When Kestrel is configured to listen on a port, Kestrel handles all traffic for that port regardless of requests' `Host` headers. A reverse proxy that can share ports can forward requests to Kestrel on a unique IP and port.

A reverse proxy:

* Can limit the exposed public surface area of the apps that it hosts.
* Provide an additional layer of configuration and defense.
* Might integrate better with existing infrastructure.
* Simplify load balancing and secure communication (HTTPS) configuration. Only the reverse proxy server requires an X.509 certificate, and that server can communicate with the app's servers on the internal network using plain HTTP.

> [!WARNING]
> Hosting in a reverse proxy configuration requires [host filtering](xref:fundamentals/servers/kestrel/host-filtering).

## Resources

[proxy load balancer]<https://host-and-deploy/proxy-load-balancer>
[Kestrel vs IIS+Kestrel (reverse proxy) vs Nginx]<https://stackoverflow.com/questions/55680428/kestrel-vs-iiskestrel-reverse-proxy-vs-nginx>
[reverse-proxy]<https://www.cloudflare.com/en-gb/learning/cdn/glossary/reverse-proxy/>
