# action-dotnet-pack
An action that can be used to run the `dotnet pack` command on a list of projects, assigning to each of them the same version.

## Usage
By default, this action requires the build to be up to date for the given `build-configuration`.
To that purpose, you can use [EasyDesk/action-dotnet-build](https://github.com/EasyDesk/action-dotnet-build).
Otherwise, you can force a new build with `skip-build: false`.

### Usage example
```yaml
    steps:
      - uses: EasyDesk/action-dotnet-pack@v1
        with:
          # (Required) The list of project names for which to create packages separately.
          # Must be whitespace or newline separated.
          project-names: |
            <project-1>
            <project-2>

          # (Required) The version of the packages to create.
          # If the version starts with the 'v' prefix, it will be removed to conform to the requirements of dotnet pack.
          package-version: 1.0.0

          # (Required) The directory where the .nupkg files will be put.
          output-dir: <your-output-dir>

          # (Optional) The build configuration.
          # If not specified, defaults to 'Release'.
          build-configuration: Release

          # (Optional) Whether to skip the build using the '--no-build' flag.
          # If not specified, defaults to true.
          skip-build: true
```