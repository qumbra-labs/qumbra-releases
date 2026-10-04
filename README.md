# Qumbra releases

> [中文](README-zh.md)

Signed release binaries of the Qumbra wallets. This repository holds **no source code**. It is where the wallets' builds are published, with a checksum beside every file.

Each product has its own tags:

| Product | Tag form | Files |
|---|---|---|
| Qumbra Wallet for Mac | `macos-vX.Y.Z` | `QumbraWalletMac-X.Y.Z.dmg`, `.zip`, and a `.sha256` for each |

The other wallets (browser extension, desktop, iOS, Android) publish here too as their releases become public.

**Testnet.** Current releases connect to Qumbra test networks. Their coins and assets are **test money** and have no value.

## Verifying a download

1. **Checksum.** In the folder that holds both files:

   ```sh
   shasum -a 256 -c QumbraWalletMac-X.Y.Z.dmg.sha256
   ```

   It must print `OK`. The release notes repeat the SHA-256 values.

2. **Signature and notarization (macOS).** Builds are signed with a Developer ID certificate of Apple team `CMV44JGUS3`, notarized by Apple, and stapled. After you mount the DMG:

   ```sh
   spctl -a -vv "/Volumes/Qumbra Wallet for Mac X.Y.Z/Qumbra Wallet for Mac.app"
   ```

   The result must read `accepted` and `source=Notarized Developer ID`, and the `origin=` line must end in `(CMV44JGUS3)`. Do not run a build that fails either check.

## What a release states

Each release lists the source revisions it was built from, the toolchain, the Apple notarization submission IDs, and the SHA-256 of every file. Open-source license notices ship inside each app. On macOS they are under **Settings → About → Open-Source Licenses**.
