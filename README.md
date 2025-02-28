# Crowdin CLI Standalone

This repository contains native binaries of the Crowdin CLI built using GraalVM.

## Overview

The Crowdin CLI is a Java-based command-line tool for interacting with Crowdin. This repository provides native binaries built from the official Crowdin CLI JAR using GraalVM, which offers several advantages:

- No Java runtime required
- Faster startup time
- Smaller distribution size
- Platform-specific binaries

## Supported Platforms

The following platforms are supported:

- Linux (x86_64)
- Linux (ARM64)
- macOS (x86_64)
- macOS (ARM64)
- Windows (x86_64)

## Usage

These binaries are primarily used by the [setup-crowdin-cli](https://github.com/IlyaGulya/setup-crowdin-cli) GitHub Action to provide a fast and efficient way to use Crowdin CLI in GitHub Actions workflows.

You can also download and use these binaries directly from the [Releases](https://github.com/IlyaGulya/crowdin-cli-standalone/releases) page.

## Build Process

The build process consists of the following steps:

1. Download the official Crowdin CLI JAR from the [Crowdin CLI repository](https://github.com/crowdin/crowdin-cli)
2. Strip AWT dependencies using the custom Stripper tool
3. Compile and package the reflection feature
4. Build native binaries using GraalVM
5. Test the binaries
6. Create a GitHub release with the binaries

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

- [Crowdin CLI](https://github.com/crowdin/crowdin-cli) - The official Crowdin CLI
- [GraalVM](https://www.graalvm.org/) - The native image builder 
