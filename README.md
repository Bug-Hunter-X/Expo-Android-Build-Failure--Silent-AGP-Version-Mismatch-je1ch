# Expo Android Build Failure: Silent AGP Version Mismatch

This repository demonstrates a common, yet difficult-to-diagnose, issue encountered when building Android apps with the Expo CLI. The problem stems from a mismatch between the Android Gradle Plugin (AGP) version declared in your project and the version required by Expo's underlying build system. The error manifests as a generic Gradle build failure without explicitly mentioning the AGP version conflict.

## Reproducing the Bug

The `expo_agp_bug.js` file contains a minimal Expo project setup that's likely to trigger the AGP version mismatch error. Steps to reproduce:

1. Clone this repository.
2. Navigate to the project directory.
3. Run `expo prebuild`.  If successful, proceed to step 4. If this fails, you might need to adjust the AGP version in the gradle-wrapper.properties file for the error to occur. 
4. Run `expo build:android`. Observe the build failure (check the log for Gradle errors). Note that successful `expo prebuild` does not mean the build is good to go, this only means that the project setup and expo dependencies are okay, build errors could still happen. 

## Solution

The solution, provided in `expo_agp_solution.js`, involves carefully examining the AGP version in `android/gradle/wrapper/gradle-wrapper.properties` and aligning it with the version compatible with your Expo CLI version. This often involves checking Expo's documentation for the recommended AGP version.  It may be necessary to update the AGP to a later version which may be a more stable and up-to-date version which also fixes the issue. You might also need to adjust the version in your project's `build.gradle` files.