Run keosd with these options:

```
--http-server-address=0.0.0.0:5555
```

Run nodeos with these options:

```
-e -p eosio \
  --plugin eosio::producer_plugin \ 
  --plugin eosio::history_plugin \
  --plugin eosio::chain_api_plugin \
  --plugin eosio::history_plugin \
  --plugin eosio::history_api_plugin \ 
  --plugin eosio::http_plugin \
  --access-control-allow-origin=* \
  --contracts-console \
  --http-validate-host=false \ 
  --filter-on=* \
  --hard-replay-blockchain
```

## Clean restart

```
rm -rf ~/.local/share/eosio ~/eosio-wallet
```