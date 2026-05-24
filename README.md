# keccak-php

Keccak-256 and SHA-3 family permutations in pure PHP — the hash primitive used across Ethereum (`keccak256`) and other modern chains.

## Status

Pre-1.0. Public API may change before the 1.0 tag.

## Install

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

## Reference

Keccak / SHA-3 specification: <https://keccak.team/>

## License

MIT License.
