# Docker Reverse Proxy for Local Development

Offer a mapping for various apps. Automagically detect containers and create reverse proxy for them.  
Uses `nginxproxy/nginx-proxy` image. that's where the magic happens. This is just a docker-compose wrapper.

To run it, simply use the following command:

- `docker compose -p reverse-proxy-local up -d`

Other images locally should expose the port and a virtual hostname, for example in this excerpt of a docker-compose file:

```
[...]
some_service:
    image: something/something
    expose:
      - "8000"
    environment:
      - VIRTUAL_HOST=something.local
      - VIRTUAL_PORT=8000
```

On windows at least, any custom domain that is offered via reverse proxy needs to be added to your local `hosts` file in Windows (not the WSL) anyway or your browser won't be able to find it.

If you run into any problem with networking, first thing to try is run `docker network prune` to remove the unused docker networks.

For more informations: https://github.com/nginx-proxy/nginx-proxy
