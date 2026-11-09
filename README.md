# DCU encrypted firmware releases

Public release assets contain AES-256-GCM encrypted MCUboot-signed firmware and a version index (`latest.json`). Use the compatible DCU mobile app to check versions, download, decrypt, and update via MCUmgr SMP over BLE.

Source code, plaintext firmware binaries, encryption keys, signing keys, and the mobile APK are not published in this repository.

## Package format

- `DCU-<version>.bin.enc`: ciphertext followed by the 16-byte GCM authentication tag.
- `latest.json`: product/hardware/version, plaintext length/SHA-256 and encryption metadata (algorithm, key ID, 12-byte nonce, ciphertext length/SHA-256 and URL).
- Authenticated additional data (UTF-8): `DCU|raytac-mdbt50q-db-40|<major.minor.patch+build>`.

Public latest index: https://github.com/dayfeather/dcu-firmware-releases/releases/latest/download/latest.json

Downloading a package does not authorize installing arbitrary firmware. The compatible bootloader retains its signature checks. Encryption is separate from the firmware signature.
