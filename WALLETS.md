# Wallets

## Useful commands

```

# Set up an alias to match the port that runs keosd

cls() { /home/james/eosinstall/bin//cleos \
  --wallet-url http://127.0.0.1:5555  $* ; }

cls wallet list

```

```
james@tapi:~/git/eos/build$ cls wallet list
Wallets:
[]
```

Create a brand new wallet called "default"
```
james@tapi:~/git/eos/build$ cls wallet create
Creating wallet: default
Save password to use in the future to unlock this wallet.
Without password imported keys will not be retrievable.
"PW5JApbvqskfS6KyhsYn2WgfTEv4zh8wPv32Y8gWoVDZn6hx1tgad"
james@tapi:~/git/eos/build$ 
```

Unlock:

```
james@tapi:~/git/eos/build$ cls wallet create
Creating wallet: default
Save password to use in the future to unlock this wallet.
Without password imported keys will not be retrievable.
"PW5JApbvqskfS6KyhsYn2WgfTEv4zh8wPv32Y8gWoVDZn6hx1tgad"

james@tapi:~/git/eos/build$ cls wallet create_key
Error 3120003: Locked wallet
Ensure that your wallet is unlocked before using it!

# The password won't show up in output
james@tapi:~/git/eos/build$ cls wallet unlock
password: Unlocked: default

james@tapi:~/git/eos/build$ cls wallet list
Wallets:
[
  "default *"
]

james@tapi:~/git/eos/build$ cls wallet create_key
Created new private key with a public key of: "EOS7K4MxixvtMrP6XfrnbQ1DBK1BPtLZRTk8oPp7TjEzvV5mNLfmc"
```

```
cls wallet import
```

Create the bob and alice accounts from the tutorial:

```
cls create account eosio bob EOS7K4MxixvtMrP6XfrnbQ1DBK1BPtLZRTk8oPp7TjEzvV5mNLfmc
cls create account eosio alice EOS7K4MxixvtMrP6XfrnbQ1DBK1BPtLZRTk8oPp7TjEzvV5mNLfmc
cls create account eosio hello EOS7K4MxixvtMrP6XfrnbQ1DBK1BPtLZRTk8oPp7TjEzvV5mNLfmc -p eosio@active
```