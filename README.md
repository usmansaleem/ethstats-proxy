# Caddy as reverse proxy for ethstats server.

## Git clone
```
git clone https://github.com/usmansaleem/ethstats-proxy.git
git submodule update --init --recursive
```

## Docker compose
```
docker compose up
```

## Besu with ethstats.

Fix the path for caddy ca cert as per your environment.

```
./besu --network=dev --miner-enabled --miner-coinbase=0xfe3b557e8fb62b89f4916b721be55ceb828dbd73 \
--rpc-http-cors-origins="all" --host-allowlist="*" --rpc-ws-enabled --rpc-http-enabled \
--data-path=/tmp/tmpDatdir \
--ethstats=test-node-1:test@localhost \
--ethstats-contact=test@test --ethstats-cacert-file=$HOME/work/ethstats-proxy/data/caddy/pki/authorities/local/root.crt
```

## Browser
```
http://localhost:3000
Or (via https - with invalid cert warnings)
https://localhost 
```