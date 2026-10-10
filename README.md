# LATTICE Android Smoke Build 001

Standalone native Kotlin Android build test for LATTICE. The launcher displays
the smoke build identifier. This repository does not change BUILD_0009 or
implement BUILD_0010.

- Application ID: `com.lattice.smoke`
- Version: `0.0.1-smoke001` (version code 1)
- Minimum Android: API 23; target/compile: API 35
- Toolchain: Java 17, Gradle 8.9, Android Gradle Plugin 8.7.3, Kotlin 2.0.21

## Build

With Java 17, Gradle 8.9 and an Android SDK installed:

```sh
gradle --no-daemon --stacktrace :app:assembleDebug :app:lintDebug
```

APK output: `app/build/outputs/apk/debug/app-debug.apk`.

## GitHub Actions delivery

The `Android Smoke Build 001` workflow runs on pushes to `main` and can also
be started manually using **Run workflow** in GitHub.

The workflow builds the real APK, runs Android lint, verifies the APK signature
and package metadata, and uploads:

- `LATTICE-Android-Smoke-Build-001-APK`: APK, SHA-256, package/signature reports,
  commit/run evidence JSON and lint reports.
- `LATTICE-Android-Smoke-Build-001-Build-Log`: Gradle log, including on failure.

The APK is signed with the CI-generated Android **debug key** and is for testing.
An artifact upload or repository commit alone is not proof of a successful build.
Use the successful run, verification steps, downloadable APK and SHA-256 together.
Installing and launching on a device is a separate verification step.
