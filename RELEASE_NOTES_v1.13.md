# Smartie Coin Classic v1.13.0 Release Notes

## About

Smartie Coin Classic is the original Smartiecoin chain, preserved and maintained by community request. This release rebrands the project to **Smartie Coin Classic** and includes important bug fixes and modernization updates while keeping the blockchain and consensus rules completely unchanged.

No chain reset. No protocol changes. Your existing wallet and blockchain data will continue to work as-is.

## What's New

### Rebrand to Smartiecoin Classic
- All GUI strings, window titles, tooltips, and about dialogs updated to "Smartiecoin Classic"
- Application name updated to `SmartieCoinClassic-Qt`
- Copyright updated to 2026
- Repository renamed from `smartiecoin-legacy` to `Smartiecoin-Classic`

### Ticker Change: SMARTIE → SMTC
- Currency unit changed from `SMARTIE` to `SMTC` across all RPC, GUI, and CLI output
- Updated denomination references: `0.01 SMTC`, `0.1 SMTC`, `1 SMTC`, `10 SMTC`
- Updated masternode collateral display to `1000 SMTC`
- This is a cosmetic-only change — no consensus or protocol impact

### Complete Cosmetic Rebranding (32 files)
All non-copyright references to "Smartiecoin Core" replaced with "Smartiecoin Classic":
- **GUI:** About dialog, splash screen, address book, send dialog, RPC console, PrivateSend help, intro/welcome screen, shutdown window
- **Daemon/CLI:** Startup messages, stop/shutdown messages, version strings
- **Error messages:** Lock file warnings, wallet version errors, sanity check failures, clock warnings, network connection errors
- **RPC:** Help text, mining error messages, wallet dump headers
- **Build system:** Consensus library metadata (`libsmartiecoinconsensus.pc.in`), Windows resource file
- **Startup shortcuts:** Windows Start Menu and Linux `.desktop` entry names
- **Block explorer:** Deployed at `explorer.smartiecoinclassic.com` with SMTC branding

### Bug Fixes

#### OpenSSL 3.0 Compatibility (Critical)
- Removed deprecated `EVP_CIPHER_CTX_init()` and `EVP_CIPHER_CTX_cleanup()` calls in wallet encryption code
- The wallet now compiles cleanly with OpenSSL 3.0+ which is standard on modern Linux distributions (Ubuntu 22.04+, Debian 12+, etc.)
- Previously, the wallet would fail to compile on systems with OpenSSL 3.0

#### Deprecated Boost API Cleanup
- Replaced `BOOST_FOREACH` with modern C++11 range-based for loops in wallet encryption
- Removed unnecessary `boost/foreach.hpp` include

#### Modern C++ Compliance
- Replaced all `NULL` with `nullptr` in wallet code (16 instances) for C++11 compliance
- Prevents potential type-safety issues with null pointer usage

#### Buffer Safety
- Replaced unsafe `sprintf` with `snprintf` in `uint256.cpp` to prevent potential buffer overflows

#### Build System Fixes
- Fixed `SMARITECOIN` typo in `configure.ac` header guard
- Updated version to 1.13.0 consistently across `clientversion.h` and `configure.ac`
- Updated issue tracker URL to new repository

### What's NOT Changed (Preserved)
- Consensus rules - identical to the original chain
- Network protocol and ports (mainnet: 8283)
- Genesis block and chain parameters
- Masternode functionality
- Wallet file format - existing wallets work without changes
- DNS seed nodes

## Downloads

- **Windows (64-bit):** `smartiecoin-classic-1.13.0-win64.zip`
- **Linux (64-bit):** `smartiecoin-classic-1.13.0-linux64.tar.gz`

### Included Binaries
- `smartiecoinclassicd` / `smartiecoinclassicd.exe` — Daemon
- `smartiecoinclassic-cli` / `smartiecoinclassic-cli.exe` — RPC client
- `smartiecoinclassic-qt` / `smartiecoinclassic-qt.exe` — Qt GUI wallet
- `smartiecoin-tx` / `smartiecoinclassic-tx.exe` — Transaction utility

## Building from Source

See the `doc/` directory for platform-specific build instructions.

## Links

- GitHub: https://github.com/SmartiesCoin/Smartiecoin-Classic
- Discord: https://discord.gg/smartiecoin
- Website: https://smartiecoin.com
