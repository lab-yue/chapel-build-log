# Resource

## net


[servo / hosts.rs](https://github.com/servo/servo/blob/master/components/net/hosts.rs)

rust:

```
pub fn parse_hostsfile(hostsfile_content: &str) -> HashMap<String, IpAddr> {
    hostsfile_content
        .lines()
        .filter_map(|line| {
            let mut iter = line.split('#').next().unwrap().split_whitespace();
            Some((iter.next()?.parse().ok()?, iter))
        })
        .flat_map(|(ip, hosts)| {
            hosts
                .filter(|host| {
                    let invalid = [
                        '\0', '\t', '\n', '\r', ' ', '#', '%', '/', ':', '?', '@', '[', '\\', ']',
                    ];
                    host.parse::<Ipv4Addr>().is_err() && !host.contains(&invalid[..])
                })
                .map(move |host| (host.to_owned(), ip))
        })
        .collect()
}

```
JS:

```
net.isIP(input)

Tests if the input is an IP address. Returns 0 for invalid strings, 4 for IP version 4 addresses, and 6 for IP version 6 addresses.

// In express:
var isIP = require('net').isIP;  
var subdomains = !isIP(hostname)
    ? hostname.split('.').reverse()
    : [hostname];

```

## express 

`dependency`: [express dependency](https://gist.github.com/rainy-me/b0ee1ac3dc12e2c610a54f7d079b68c4)

## Moudule serve-static

### serve-static

[serve-static](https://github.com/expressjs/serve-static)

### mime

`mime `: [mime](https://github.com/broofa/node-mime)

### url, parseurl, encodeurl

`url handling`: [Crate url](https://docs.rs/url/1.6.0/url/index.html)

### escape-html

`escape-html`: [escape.rs](https://github.com/rust-lang/rust/blob/master/src/librustdoc/html/escape.rs)

### path

`Filesystem`: [Module std::fs](https://doc.rust-lang.org/std/fs/index.html)

### send

[send](https://github.com/pillarjs/send)

## Moudule status code

### statuses

[statuses](https://github.com/jshttp/statuses)
