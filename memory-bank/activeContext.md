# Active Context: Crowdin CLI Standalone

## Current Work Focus

We are currently focused on moving the native binary build process to a separate repository:

1. **Repository Separation**
   - Moving the native binary build process to a separate repository
   - Creating a clean structure for the new repository
   - Ensuring that all necessary files are included
   - Updating references to the repository in the workflow files

2. **Workflow Updates**
   - Updating the GitHub workflow files to use the new repository
   - Removing the "executable-" prefix from release tags
   - Simplifying the release process

3. **Documentation**
   - Creating comprehensive documentation for the new repository
   - Explaining the build process
   - Providing usage instructions

## Recent Changes

- Created a new directory structure for the native binary build process
- Copied all necessary files to the new directory
- Updated the GitHub workflow files to use the new repository
- Removed the "executable-" prefix from release tags
- Created a README.md file for the new repository
- Created a LICENSE file for the new repository
- Created a .gitignore file for the new repository
- Created a .gitattributes file for the new repository

## Next Steps

1. **Move to New Repository**
   - Create a new repository on GitHub
   - Push the files to the new repository
   - Set up the necessary secrets and variables

2. **Test the Workflow**
   - Trigger the workflow manually to build a specific version
   - Verify that the binaries are built correctly
   - Verify that the GitHub release is created correctly

3. **Update the Setup Action**
   - Update the setup action to download binaries from the new repository
   - Test the setup action with the new repository

## Active Decisions and Considerations

1. **Repository Structure**
   - Keeping the directory structure simple and clean
   - Including all necessary files for the build process
   - Providing comprehensive documentation

2. **Workflow Updates**
   - Removing the "executable-" prefix from release tags for simplicity
   - Updating the repository references in the workflow files
   - Ensuring that the workflow works correctly with the new repository

3. **Documentation**
   - Providing clear and comprehensive documentation
   - Explaining the build process
   - Providing usage instructions 