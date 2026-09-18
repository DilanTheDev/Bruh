# Discord APK Decompilation

## Source
- URL: https://apkpure.com/discord/com.discord
- Downloaded via: APKPure CDN (`https://d.cdnpure.com/b/APK/com.discord?version=latest`)

## APK Info
- **Package**: `com.discord`
- **Version**: 345.9 - Stable (versionCode: 345009)
- **APK Size**: ~103 MB
- **compileSdkVersion**: 36 (Android 16)

## Permissions (from AndroidManifest.xml)
- `INTERNET`
- `CAMERA`
- `RECORD_AUDIO`
- `MODIFY_AUDIO_SETTINGS`
- `READ_MEDIA_IMAGES`, `READ_MEDIA_VIDEO`, `READ_MEDIA_AUDIO`
- `FOREGROUND_SERVICE` / `FOREGROUND_SERVICE_MEDIA_PROJECTION`
- `ACCESS_NETWORK_STATE`

## Decompilation Tools Used

### apktool (v2.7.0)
- Decoded `AndroidManifest.xml`
- Decoded resource XMLs (3,512 files in `res/`)
- Extracted raw DEX files: `classes.dex`, `classes2.dex`, `classes3.dex`
- Extracted assets (React Native bundle: `assets/index.android.bundle`)

Command used:
```bash
apktool d discord.apk -o discord_decompiled --no-src
```

### jadx (v1.5.0)
- Decompiled all 3 DEX files to Java source
- **13,866** Java source files across **682** packages
- Note: code is heavily obfuscated (single-letter package names like `a`, `b`, `c`, ...)
- Recognizable third-party packages: `okhttp3`, `okio`, `kotlin`, `kotlinx`, `androidx`, `com`, `org`, `net`

Command used:
```bash
jadx --output-dir discord_jadx --threads-count 4 discord.apk
```

## Output Location
Decompiled output is in the scratchpad (not committed to repo due to size):
- `scratchpad/discord_decompiled/` — apktool output (resources, manifest)
- `scratchpad/discord_jadx/` — jadx output (Java source)

## Notes
- The app uses React Native (JS bundle at `assets/index.android.bundle`)
- Native libs in `lib/` for arm64-v8a, armeabi-v7a, x86, x86_64
- 40 minor jadx decompilation errors (mostly zip-bomb false positive on a compressed patch asset)
