# James Moore's EOS developer notes

## What version of EOS does this cover?

FAQ Updated Sat Aug 11 09:58:31 PDT 2018.

Latest commit is:

```
commit 4f4e5c225afa4d4e82cb8283074d8311a0178887 (HEAD -> master, tag: v1.1.4, origin/master, origin/HEAD)
Merge: ad4ba2831 e1d074016
Author: wanderingbort <bart.wyatt@block.one>
Date:   Tue Aug 7 20:16:11 2018 -0400

    Merge pull request #5098 from EOSIO/release/1.1.x
    
    Release 1.1.4
```

## How do I configure CLion for EOS development (eos itself, not contracts)?

* Find the options that eosio_build.sh uses

Normally (not using CLion), you build eos using the 
eosio_build.sh script. CLion wants to run cmake directly, 
so you'll need to figure out the options that the build 
script passes to CMake.

I usually just run the script (in a Linux terminal) using:

    script foo -c "bash -x eosio_build.sh"

Then grep for the cmake line:

    grep cmake foo
    
On my machine, produces:

```
+ CMAKE=/home/james/.android/cmake/3.6.4111459/bin/cmake
+ /home/james/.android/cmake/3.6.4111459/bin/cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_COMPILER=clang++-4.0 -DCMAKE_C_COMPILER=clang-4.0 -DWASM_ROOT= -DCORE_SYMBOL_NAME=SYS -DOPENSSL_ROOT_DIR=/usr/include/openssl -DBUILD_MONGO_DB_PLUGIN=true -DENABLE_COVERAGE_TESTING=false -DBUILD_DOXYGEN=false -DCMAKE_INSTALL_PREFIX=/usr/local/eosio /home/james/git/eos
```

CLion will fill in some arguments. so you'll want to drop ```CMAKE_BUILD_TYPE=Release```, leaving you with:

    -DWASM_ROOT= -DCORE_SYMBOL_NAME=SYS -DOPENSSL_ROOT_DIR=/usr/include/openssl -DBUILD_MONGO_DB_PLUGIN=true -DENABLE_COVERAGE_TESTING=false -DBUILD_DOXYGEN=false -DBOOST_ROOT=/home/james/opt/boost

Then you need to see where the script put Boost:

    grep export foo
    
Produces:

```
+ export BOOST_ROOT=/home/james/opt/boost
```

Add that, and you end up with something like:

```
-DWASM_ROOT= -DCORE_SYMBOL_NAME=SYS -DOPENSSL_ROOT_DIR=/usr/include/openssl -DBUILD_MONGO_DB_PLUGIN=true -DENABLE_COVERAGE_TESTING=false -DBUILD_DOXYGEN=false -DBOOST_ROOT=/home/james/opt/boost
```

* Add those options to your CLion settings under ```CMake options```:

![CLion settings](graphics/cmakeSettingsForFAQ.png "CLion settings")
