# kong-nokia

# DB Less configuration
https://docs.konghq.com/install/docker/?_ga=2.13980855.1456939746.1594572273-1288808255.1594572273

https://docs.konghq.com/2.0.x/db-less-and-declarative-config/#the-declarative-configuration-format

https://docs.konghq.com/0.4.x/tutorials/hello-world/

https://github.com/nokia/kong-oidc

cd deploy

docker build -t kong-nokia .

docker run --rm --name kong      --network=kong-net      -v "kong-vol:/usr/local/kong/declarative"      -e "KONG_DATABASE=off"      -e "KONG_DECLARATIVE_CONFIG=/usr/local/kong/declarative/kong.yml"      -e "KONG_PROXY_ACCESS_LOG=/dev/stdout"      -e "KONG_ADMIN_ACCESS_LOG=/dev/stdout"      -e "KONG_PROXY_ERROR_LOG=/dev/stderr"      -e "KONG_ADMIN_ERROR_LOG=/dev/stderr"      -e "KONG_ADMIN_LISTEN=0.0.0.0:8001, 0.0.0.0:8444 ssl"      -p 8000:8000      -p 7443:8443      -p 127.0.0.1:8001:8001      -p 127.0.0.1:8444:8444      kong-nokia:latest