# Product Context: Crowdin CLI Standalone

## Why This Project Exists

Crowdin is a localization and translation management platform that helps teams localize their products. The Crowdin CLI is a command-line tool that allows users to interact with the Crowdin API, manage translation files, and automate localization workflows.

This project exists to solve several problems:

1. **Java Dependency**: The Crowdin CLI is a Java application, which requires a Java runtime environment. By providing native executables, we eliminate this dependency.

2. **Performance**: Native executables start faster and use less memory than Java applications.

3. **Size**: Native executables are smaller than Java applications with their runtime.

4. **Cross-Platform Compatibility**: By providing platform-specific binaries, we ensure that the CLI works correctly on different operating systems and architectures.

5. **AWT Dependencies**: The Crowdin CLI has dependencies on AWT (Abstract Window Toolkit), which can cause issues in headless environments like CI/CD pipelines. By stripping these dependencies, we improve compatibility.

## Problems It Solves

1. **Java Dependency**: Removes the requirement for Java runtime by providing native executables.

2. **Performance**: Improves startup time and reduces memory usage.

3. **Size**: Reduces the size of the distribution.

4. **Cross-Platform Compatibility**: Ensures that the CLI works correctly on different platforms.

5. **AWT Dependencies**: Removes dependencies on AWT, which can cause issues in headless environments.

## How It Works

The project works by:

1. Checking for new versions of the Crowdin CLI
2. Downloading the JAR file from the official repository
3. Stripping AWT dependencies using a custom tool
4. Building native executables using GraalVM
5. Testing the binaries to ensure they work correctly
6. Creating GitHub releases with the binaries

## User Experience Goals

1. **Simplicity**: The binaries should be easy to download and use.

2. **Reliability**: The binaries should work consistently across different environments.

3. **Performance**: The binaries should start quickly and use minimal resources.

4. **Compatibility**: The binaries should work on different platforms without additional dependencies.

5. **Documentation**: Clear documentation on how to download and use the binaries. 