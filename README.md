# amashukov/keccak-php

Pure-PHP Keccak-256, SHA-3 and SHAKE hashing — the `keccak256` primitive behind Ethereum addresses, ABI selectors and EVM signatures.

[![CI](https://img.shields.io/github/actions/workflow/status/AndreyMashukov/keccak-php/ci.yml?branch=main&label=CI)](https://github.com/AndreyMashukov/keccak-php/actions)
[![PHPStan L9](https://img.shields.io/github/actions/workflow/status/AndreyMashukov/keccak-php/stan.yml?branch=main&label=PHPStan%20L9)](https://github.com/AndreyMashukov/keccak-php/actions)
[![Latest Version](https://img.shields.io/packagist/v/amashukov/keccak-php)](https://packagist.org/packages/amashukov/keccak-php)
[![Downloads](https://img.shields.io/packagist/dt/amashukov/keccak-php)](https://packagist.org/packages/amashukov/keccak-php)
[![PHP](https://img.shields.io/packagist/dependency-v/amashukov/keccak-php/php)](https://packagist.org/packages/amashukov/keccak-php)
[![License](https://img.shields.io/packagist/l/amashukov/keccak-php)](LICENSE)
[![Stars](https://img.shields.io/github/stars/AndreyMashukov/keccak-php?style=social)](https://github.com/AndreyMashukov/keccak-php)

`amashukov/keccak-php` is a pure-PHP implementation of the Keccak / SHA-3 family of cryptographic hash functions, including the SHAKE extendable-output functions (XOF). It provides the `keccak256` hash primitive used across Ethereum and other modern blockchains for address derivation, ABI function selectors and EIP-191 / EIP-712 message signing. Zero composer dependencies — only `ext-mbstring` from PHP core.

## Features

- **Keccak-256** — the exact hash Ethereum uses for `keccak256`, address derivation and ABI selectors.
- **Full SHA-3 family** — output sizes `224`, `256`, `384`, `512`.
- **SHAKE128 / SHAKE256** extendable-output functions with arbitrary output length.
- **Hex or raw binary** output via a single `raw_output` flag.
- **Pure PHP** — no native extension to compile, no FFI; runs anywhere PHP 8.3 runs.
- **Zero composer dependencies** — `ext-mbstring` only.
- PHPStan level 9 clean, `@PER-CS` formatted, CI-tested.

## Installation

```bash
composer require amashukov/keccak-php
```

## Usage

```php
use Amashukov\Keccak\Keccak;

// Hex-encoded hash output (default).
$digest = Keccak::hash('hello world', 256);
// → 47173285a8d7341e5e972fc677286384f802f8ef42a5ec5f03bbfa254cb01fad

// Raw 32-byte binary output.
$raw = Keccak::hash('hello world', 256, raw_output: true);
```

Supported output sizes: `224`, `256`, `384`, `512`. SHAKE variants:

```php
$xof = Keccak::shake('hello world', security_level: 128, outlen: 256);
```

## Requirements

- PHP 8.3+
- `ext-mbstring`

No composer dependencies.

## Related packages

Part of a modular pure-PHP blockchain toolkit:

| Package | Purpose |
|---|---|
| [amashukov/keccak-php](https://github.com/AndreyMashukov/keccak-php) | Keccak-256 / SHA-3 / SHAKE hashing |
| [amashukov/secp256k1-php](https://github.com/AndreyMashukov/secp256k1-php) | secp256k1 ECDSA sign / verify / recover |
| [amashukov/rlp-php](https://github.com/AndreyMashukov/rlp-php) | Ethereum RLP encode / decode |
| [amashukov/ton-cell-php](https://github.com/AndreyMashukov/ton-cell-php) | TON TLB Cell / Builder / Slice / BOC |
| [amashukov/abi-encoder-php](https://github.com/AndreyMashukov/abi-encoder-php) | Ethereum ABI encoder |
| [amashukov/eip1559-tx-signer-php](https://github.com/AndreyMashukov/eip1559-tx-signer-php) | EIP-1559 transaction signer |
| [amashukov/eth-rpc-client-php](https://github.com/AndreyMashukov/eth-rpc-client-php) | Ethereum JSON-RPC client |
| [amashukov/eth-php](https://github.com/AndreyMashukov/eth-php) | EVM umbrella package |

## Quality

- PHPStan level 9.
- php-cs-fixer with the `@PER-CS` ruleset.
- GitHub Actions CI on every push.
- Test vectors validated against the published Keccak / SHA-3 reference outputs.

## License

MIT License.
