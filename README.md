# Better Contacts Helper

Swift CLI helper binary for the [Better Contacts](https://github.com/raycast/extensions/tree/main/extensions/better-contacts) Raycast extension.

## What is this?

This repository exists solely to build and distribute the Swift helper binary used by the Better Contacts Raycast extension. The actual extension code lives in the [raycast/extensions](https://github.com/raycast/extensions) repository.

## Why a separate repo?

Raycast extensions cannot bundle opaque binaries. This repo provides:
- **Transparent source code** - You can audit exactly what the binary does
- **Reproducible builds** - GitHub Actions builds the binary from source
- **Signed releases** - Each release includes SHA256 checksums for verification

## How it works

1. The Better Contacts extension downloads the helper binary from this repo's GitHub Releases
2. It verifies the SHA256 checksum before using it
3. The binary syncs your macOS Contacts to a local SQLite cache for fast searching

## Building locally

```bash
swift build -c release
```

The binary will be at `.build/release/contacts-helper`.

## Commands

```
contacts-helper status              # Check authorization status and cache age
contacts-helper sync                # Sync contacts from Contacts.app to SQLite cache
contacts-helper get <id>            # Get a single contact by identifier
contacts-helper delete <id>         # Delete a contact
contacts-helper invalidate-cache    # Clear the cache
contacts-helper db-path             # Print the database path
```

## License

MIT
