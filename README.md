# kong-nokia

# DB Less configuration
https://docs.konghq.com/install/docker/?_ga=2.13980855.1456939746.1594572273-1288808255.1594572273

https://docs.konghq.com/2.0.x/db-less-and-declarative-config/#the-declarative-configuration-format

https://docs.konghq.com/0.4.x/tutorials/hello-world/

cd deploy

docker build -t kong-nokia .

docker run --name kong \
    --link kong-database:kong-database \
    -e "KONG_DATABASE=postgres" \
    -e "KONG_PG_HOST=kong-database" \
    -e "KONG_PROXY_ACCESS_LOG=/dev/stdout" \
    -e "KONG_ADMIN_ACCESS_LOG=/dev/stdout" \
    -e "KONG_PROXY_ERROR_LOG=/dev/stderr" \
    -e "KONG_ADMIN_ERROR_LOG=/dev/stderr" \
    -e "KONG_ADMIN_LISTEN=0.0.0.0:8001, 0.0.0.0:8444 ssl" \
    -p 7000:8000 \
    -p 7443:8443 \
    -p 7001:8001 \
    -p 7444:8444 \
    kong-nokia:latest