# Mikatsu Build Instructions

## Prerequisites
- Android Studio (latest version)
- JDK 17 or higher
- Android SDK (API 34+)

## Building the APK

### Option 1: Android Studio
1. Open Android Studio
2. File → Open → Select the `mikatsu` folder
3. Wait for Gradle sync to complete
4. Build → Build Bundle(s) / APK(s) → Build APK(s)
5. APK will be in: `app/build/outputs/apk/standard/release/`

### Option 2: Command Line
```bash
cd /home/claude/mikatsu

# Debug build (for testing)
./gradlew assembleStandardDebug

# Release build (for distribution)
./gradlew assembleStandardRelease

# Output location:
# Debug: app/build/outputs/apk/standard/debug/app-standard-debug.apk
# Release: app/build/outputs/apk/standard/release/app-standard-release.apk
```

## Signing the Release APK

### Generate signing key:
```bash
keytool -genkey -v -keystore mikatsu-release-key.jks \
    -alias mikatsu -keyalg RSA -keysize 2048 -validity 10000
```

### Sign the APK:
```bash
jarsigner -verbose -sigalg SHA256withRSA -digestalg SHA-256 \
    -keystore mikatsu-release-key.jks \
    app/build/outputs/apk/standard/release/app-standard-release-unsigned.apk \
    mikatsu
```

## Installation
```bash
adb install app/build/outputs/apk/standard/debug/app-standard-debug.apk
```

## Troubleshooting

### Gradle sync fails:
- Check internet connection
- Update Android Gradle Plugin
- Invalidate caches: File → Invalidate Caches / Restart

### Build fails:
- Clean project: Build → Clean Project
- Rebuild: Build → Rebuild Project
- Check JDK version: File → Project Structure → SDK Location

### Package conflicts:
- Uninstall old Mihon/Tachiyomi first
- Clear app data if upgrading
