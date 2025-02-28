# Project Brief: Crowdin CLI Standalone

## Overview
This project creates native binaries of the Crowdin CLI using GraalVM for cross-platform compatibility. It provides standalone executables that can be used without a Java runtime environment.

## Core Requirements
1. Create a GitHub workflow that periodically checks for Crowdin CLI updates
2. Build native executables using GraalVM for cross-platform compatibility
3. Strip AWT dependencies to reduce binary size and improve compatibility
4. Test the binaries to ensure they work correctly
5. Create GitHub releases with these executables
6. Provide a clear and simple way to download and use the binaries

## Success Criteria
- Automated detection of new Crowdin CLI versions
- Successful building of native executables for multiple platforms
- Proper GitHub releases with versioned assets
- Binaries that work correctly without a Java runtime
- Comprehensive documentation for users

## Constraints
- Must follow GitHub Actions best practices
- Should handle cross-platform compatibility
- Must be efficient and reliable
- Should support only Crowdin CLI versions 4.4.0 and above

## Timeline
- Initial implementation: Create the workflow for building and releasing
- Testing: Ensure the binaries work as expected
- Documentation: Provide clear usage instructions
- Release: Publish the binaries to GitHub Releases 