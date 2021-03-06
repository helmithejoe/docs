---
author:
  name: Linode
  email: docs@linode.com
description: 'Mapping aliases, domains or hostnames to IP addresses using the system hosts file.'
keywords: 'hosts,hosts file,hostname,alias'
license: '[CC BY-ND 4.0](https://creativecommons.org/licenses/by-nd/4.0)'
modified: Thursday, September 14th, 2017
modified_by:
  name: Linode
published: 'Thursday, September 14th, 2017'
title: Using Your System's hosts File
---

The Linux [hosts file](http://man7.org/linux/man-pages/man5/hosts.5.html) lives at `/etc/hosts`, and creates static associations between IP addresses and hostnames, domains or machine aliases. Your Linode then gives those associations higher priority than hostnames or domains which must be resolved by DNS.

There are many different ways to use entries in the hosts file, and the types of associations you set would depend on your specific use case. Below are some examples.

- Map the alias `mywebsite` to a given IP address:

      203.0.113.10 mywebsite

- Map the domain `example.com` to the given IP address. This is often done when hosting a web or mail server.

      203.0.113.10 example.com

- Combine the two options above, so both the domain and the alias map to the IP address:

      203.0.113.10 example.com mywebsite

- Map the alias `backupserver` to a given private IPv6 address:

      fe80::f03c:91ff:fe24:3a2f backupserver

- Set a [fully qualified domain name](https://en.wikipedia.org/wiki/Fully_qualified_domain_name) (FQDN). In the example below, replace *hostname* with your system's hostname. The domain *example.com* can be a public internet domain (ex. a public website) or the domain of a private network (ex. your home LAN), or a subdomain (subdomain.example.com). It's important to add the FQDN entry directly after the localhost line, so the end result would look like:

      127.0.0.1 localhost
      127.0.1.1 hostname.example.com hostname

    A FQDN does not necessarily need to have any relationship to websites or other services hosted on the server (although it may if you wish). As an example, you might host `www.something.com` on your server, but the system’s FQDN might be `mars.somethingelse.com`.

    The domain you assign as your system’s FQDN should have an “A” record in DNS pointing to your Linode’s IPv4 address. For IPv6, you should also set up a “AAAA” record in DNS pointing to your Linode’s IPv6 address. For more information on configuring DNS, see our guide on [DNS records](/docs/networking/dns/dns-records-an-introduction).