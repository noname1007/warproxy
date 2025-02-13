# WARProxy

Use Cloudflare WARP as your socks5 proxy server with one click.

Includes:
- WGCF: generate cf warp accounts and wireguard config automatically.
- WireProxy: create socks5 proxy.
- Warp+: refresh warp+ traffic.
- Health check etc.

## Usage

```yaml
services:
  warproxy:
    image: ghcr.io/kingcc/warproxy:latest
    restart: always
    environment:
      - WARP_PLUS=true
      - ENDPOINT=162.159.192.12
      - DNS=223.5.5.5
    ports:
      - 1080:1080
```

### To change license key
If you have an existing Warp+ license key, edit `/config/wgcf-account.toml` and,  delete two files :  
`/config/wgcf-profile.conf` and `/config/wireproxy.conf`  
When you restart container, it will update your account info and re-generate conf files automatically.


## Environment variables

| ENV  | Description  | Default  |
|---|---|---|
| ```PUID``` / ```PGID```  | uid and gid for running an app  | ```911``` / ```911```  |
| ```TZ```  | timezone  | ```Asia/Shanghai```  |
| ```PROXY_PORT```  | to run proxy in a different port  | ```1080``` |
| ```USERNAME```  | username of socks5 auth  |  |
| ```PASSWORD```  | password of socks5 auth  |  |
| ```DNS```  | dns options of wire-proxy  | ```1.1.1.1``` |
| ```ENDPOINT```  | endpoint of cloudflare | ```engage.cloudflareclient.com``` |
| ```WARP_PLUS```  | set ```true``` to enable auto WARP+ quota script  | ```false``` |
| ```WARP_PLUS_VERBOSE```  | set ```true``` to run auto WARP+ quota script in verbose mode   | ```false```  |


## Thanks
* [105PM](https://github.com/105PM/docker-warproxy)
* [by275 (docker-dpitunnel)](https://github.com/by275/docker-dpitunnel)