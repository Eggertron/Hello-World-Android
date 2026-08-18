# Android Hello World App

A simple "Hello World" Android application built using **Kotlin**. This project serves as a foundational template for Android development and includes an automated GitHub Actions CI/CD pipeline that dynamically generates the Gradle wrapper and builds the APK.

## Project Structure

- `app/`: Contains the core Android application source code, resources, and Gradle configuration.
- `.github/workflows/`: Contains the automated CI/CD pipeline configuration.

## Prerequisites

- Android SDK (automatically handled by the build environment/CI)
- Java Development Kit (JDK) 17 or higher
- Gradle (managed dynamically via the CI workflow or locally via an existing Gradle installation)

## Building Locally

To build the application locally from your terminal, you will need to generate the wrapper files once (if they aren't tracked in your repository) by running:

```bash
# Generate the wrapper (requires Gradle installed locally)
gradle wrapper

# Make gradlew executable (Linux/macOS)
chmod +x gradlew

# Build the debug APK
# On Linux/macOS
./gradlew assembleDebug

# On Windows
gradlew.bat assembleDebug
```

The resulting APK will be generated at: app/build/outputs/apk/debug/app-debug.apk
GitHub Actions CI/CD
This repository is configured with an automated workflow to build the project on every push and pull request to the main or master branches.
Workflow Process:
 * Trigger: A push or pull request to the main or master branch.
 * Setup: The workflow sets up an Ubuntu virtual machine, installs JDK 17, and caches dependencies for speed.
 * Generate Wrapper: Automatically generates the Gradle wrapper (gradlew) directly on the runner.
 * Build: The workflow executes ./gradlew assembleDebug to compile the Kotlin code and package the APK.
 * Artifacts: The resulting app-debug.apk file is uploaded as a build artifact to the GitHub Action run.
How to Retrieve Build Artifacts:
 * Navigate to the Actions tab in your GitHub repository.
 * Click on the desired workflow run.
 * Scroll down to the Artifacts section at the bottom of the page.
 * Click on app-debug-apk to download the APK.

