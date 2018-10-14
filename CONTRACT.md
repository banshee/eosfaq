Create an account for the contract:

```
cls create account eosio addressbook EOS7K4MxixvtMrP6XfrnbQ1DBK1BPtLZRTk8oPp7TjEzvV5mNLfmc
```

```
james@tapi:~/git/eos$ cls set contract addressbook /home/james/git/eos/cmake-build-debug/contracts/address_book
Reading WAST/WASM from /home/james/git/eos/cmake-build-debug/contracts/address_book/address_book.wasm...
Using already assembled WASM...
Publishing contract...
executed transaction: 9d7a6d9a75751f11dfb736ce71d848f5f5597d1f705b3a94801ceec67ccac7c7  5752 bytes  7727 us
#         eosio <= eosio::setcode               {"account":"addressbook","vmtype":0,"vmversion":0,"code":"0061736d0100000001771360027f7e0060077f7e7f...
#         eosio <= eosio::setabi                {"account":"addressbook","abi":"0e656f73696f3a3a6162692f312e30010c6163636f756e745f6e616d65046e616d65...
warning: transaction executed locally, but may not be confirmed by the network yet    ] 
james@tapi:~/git/eos$ 
```