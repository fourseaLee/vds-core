# Copyright (c) 2017 The Bitcoin developers

project(wallet)

# Add Berkeley DB dependency.
find_package(BerkeleyDB REQUIRED)

# Add event dependency. This is only required for evhttp_uridecode
# in rpcwallet.cpp so it may be worth considering using an alternative.
find_package(Event REQUIRED)

add_library(wallet
            asyncrpcoperation_sendmany.cpp
            bip39_mnemonic.cpp
            crypter.cpp
            db.cpp
            fees.cpp
            feebumper.cpp
            rpcdisclosure.cpp
            rpcdump.cpp
            rpcwallet.cpp
            wallet.cpp
            walletdb.cpp
            wallet_ismine.cpp
            )

target_link_libraries(wallet util vds univalue Event ${BDBXX_LIBRARY})

target_include_directories(wallet PUBLIC ${BDBXX_INCLUDE_DIR})
