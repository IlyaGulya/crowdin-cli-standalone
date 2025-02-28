# Technical Context: Crowdin CLI Standalone

## Technologies Used

### Core Technologies
- **GraalVM**: For creating native executables from Java applications
- **Crowdin CLI**: The tool we're packaging and distributing
- **Java Bytecode Manipulation**: For removing AWT dependencies from the JAR
- **GitHub Actions**: For creating the workflow

### GitHub-Specific Technologies
- **GitHub Releases API**: For creating releases with assets
- **GitHub Workflow Scheduler**: For periodic checking of updates
- **GitHub Actions Matrix**: For defining build configurations
- **GitHub Actions Artifacts**: For passing files between jobs
- **GitHub Actions Concurrency**: For preventing workflow conflicts
- **GitHub Script**: For running JavaScript code in workflows
- **Octokit**: For interacting with GitHub API

### Development Tools
- **ASM**: Java bytecode manipulation library used by the AWT stripper
- **Gradle**: Build tool for the AWT stripper
- **Java**: For implementing the AWT stripper and GraalVM reflection feature

## Development Setup
- Java development environment for the AWT stripper and GraalVM reflection feature
- GitHub repository for hosting the binaries
- GitHub workflow for testing and releasing

## Technical Constraints
- Must follow GitHub Actions security best practices
- Should handle different operating systems (Linux, macOS)
- Should handle different architectures (x86_64, arm64)
- Should be efficient with GitHub Actions minutes
- Should handle matrix job failures gracefully
- Must support only Crowdin CLI versions 4.4.0 and above

## Supported Platforms
- **Linux (x86_64)**: Standard Linux on Intel/AMD 64-bit architecture
- **Linux (arm64)**: Linux on ARM 64-bit architecture (e.g., AWS Graviton)
- **macOS (x86_64)**: macOS on Intel 64-bit architecture
- **macOS (arm64)**: macOS on Apple Silicon (M1/M2/M3) architecture
- **Windows is not supported** due to compatibility issues with the native executables

## Dependencies
- Crowdin CLI (https://github.com/crowdin/crowdin-cli)
- GraalVM for native image compilation
- ASM library for Java bytecode manipulation
- Gradle for building the AWT stripper

## Build Process
1. **Check for Updates**:
   - Check for new Crowdin CLI versions
   - Determine if a build is needed

2. **Build Native Executables**:
   - Download the JAR file from the official repository
   - Run the AWT stripper to remove AWT dependencies from the JAR
   - Compile the GraalVM reflection feature
   - Use GraalVM to compile the Java application into native executables
   - Build for multiple platforms using a matrix strategy:
     - Linux (x86_64)
     - Linux (arm64)
     - macOS (x64)
     - macOS (arm64)
   - Test each binary on its native platform immediately after building

3. **Create GitHub Release**:
   - Create a version branch
   - Create a `.crowdin-version` file with the version number
   - Commit and tag changes
   - Push the tag to the repository
   - Download artifacts
   - Create a GitHub release with the binaries

## AWT Stripper

The AWT stripper is a custom tool that removes AWT dependencies from the Crowdin CLI JAR. It uses the ASM library for Java bytecode manipulation.

1. **How It Works**:
   - Reads the JAR file
   - Processes each class file
   - Replaces AWT method calls with exceptions
   - Replaces AWT field access with exceptions
   - Writes the modified JAR file

2. **Benefits**:
   - Improves compatibility in headless environments
   - Reduces binary size
   - Ensures that users understand why certain commands are not supported

## GraalVM Reflection Feature

The GraalVM reflection feature is a custom GraalVM feature that registers classes for reflection. It ensures that required classes are available at runtime.

1. **How It Works**:
   - Scans packages for classes
   - Registers classes for reflection
   - Registers constructors, methods, and fields
   - Explicitly registers problematic classes

2. **Benefits**:
   - Improves compatibility
   - Reduces issues with reflection
   - Ensures that required classes are available at runtime

## GitHub API Integration

The project uses Octokit for GitHub API interactions:

1. **Version Checking**:
   - Using Octokit to check if a release exists
   - Handling 404 errors to determine if a release needs to be created
   - Using try/catch blocks for better error handling

2. **Release Creation**:
   - Using `softprops/action-gh-release` for creating GitHub releases
   - Specifying tag name, release name, body, and files
   - Controlling whether a release is marked as latest

3. **Benefits**:
   - Better type safety and error handling
   - Simplified API calls and response handling
   - More maintainable and readable code 
