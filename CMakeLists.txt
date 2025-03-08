# 完全采用https://github.com/xtools-at/colibri/tree/main/firmware/lib/TrezorCrypto-Arduino/src的文件内容
# 缺少的nem.c,nem.h 和 nem_serialize.h 来自https://github.com/dexon-foundation/esp-trezor-crypto/tree/master,有错误已经修改
idf_component_register(
    SRCS
        # Core files
        "address.c"
        "base32.c"
        "base58.c"
        "bignum.c"
        "bip32.c"
        "bip39.c"
        "bip39_english.c"
        "blake256.c"
        "blake2b.c"
        "blake2s.c"
        "buffer.c"
        "cardano.c"
        "cash_addr.c"
        "chacha_drbg.c"
        "curves.c"
        "der.c"
        "ecdsa.c"
        "elligator2.c"
        "groestl.c"
        "hasher.c"
        "hash_to_curve.c"
        "hmac.c"
        "hmac_drbg.c"
        "memzero.c"
        "nem.c"
        "nist256p1.c"
        "pbkdf2.c"
        "rand.c"
        "rc4.c"
        "rfc6979.c"
        "ripemd160.c"
        "script.c"
        "secp256k1.c"
        "segwit_addr.c"
        "sha2.c"
        "sha3.c"
        "shamir.c"
        "slip39.c"
        "slip39_english.c"
        "tls_prf.c"

        # AES files
        "aes/aes_modes.c"
        "aes/aescrypt.c"
        "aes/aeskey.c"
        "aes/aestab.c"
        "aes/aesccm.c"
        "aes/aesgcm.c"
        "aes/gf128mul.c"

        # Ed25519-donna files
        "ed25519-donna/curve25519-donna-32bit.c"
        "ed25519-donna/curve25519-donna-helpers.c"
        "ed25519-donna/curve25519-donna-scalarmult-base.c"
        "ed25519-donna/ed25519-donna-32bit-tables.c"
        "ed25519-donna/ed25519-donna-basepoint-table.c"
        "ed25519-donna/ed25519-donna-impl-base.c"
        "ed25519-donna/ed25519-keccak.c"
        "ed25519-donna/ed25519-sha3.c"
        "ed25519-donna/ed25519.c"
        "ed25519-donna/modm-donna-32bit.c"

        # Monero files
        "monero/base58.c"
        "monero/serialize.c"
        "monero/xmr.c"

        # ChaCha20Poly1305 files
        "chacha20poly1305/chacha20poly1305.c"
        "chacha20poly1305/chacha_merged.c"
        "chacha20poly1305/poly1305-donna.c"
        "chacha20poly1305/rfc7539.c"

    INCLUDE_DIRS 
        "."
        ".."
        "aes"
        "ed25519-donna"
        "monero"
        "chacha20poly1305"

    REQUIRES 
        "mbedtls"
        "esp_hw_support"
)

target_compile_options(${COMPONENT_LIB} PRIVATE 
    -Wno-unused-function
    -Wno-unused-variable
    -Wno-sign-compare
    -Wno-strict-aliasing
    -Wno-unused-but-set-variable
    -Wno-implicit-function-declaration
    -Wno-int-conversion
    -Wno-pointer-sign
)

target_compile_definitions(${COMPONENT_LIB} PRIVATE
    USE_ETHEREUM=1
    USE_KECCAK=1
    USE_MONERO=1
    USE_NEM=1
    USE_CARDANO=1
    USE_INSECURE_PRNG=1
    AES_128=1
    AES_192=1
    AES_VAR=1
    USE_AES=1
    ED25519_CUSTOMHASH=1
    ED25519_CUSTOMRNG=1
) 