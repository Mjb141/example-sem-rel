# example-sem-rel

## Flags

`--check-if-ci` can disable the Semantic Release check to determine if it is running on a CI platform.

`--dry-run` allows you to check what Semantic Release will do.

## Usage

### Tokens

If your config file contains a plugin such as `@semantic-release/github` or `@semantic-release/gitlab` you will need the required API token (personal access token) in your environment.

If you do not have such a token you can [modify the config file](#Temporarily-modifying-the-config-file) temporarily in the `with-config` step.

**After committing and pushing your changes, do one of the following:**

To test what Semantic Release will do:

`dagger -m "github.com/mjb141/daggerverse/sem-rel@main" call with-config --branch "testbranch" release --dir . --provider "github" --token env:GH_TOKEN stdout`

To run a release from local `--dry-run=false` is required:

`dagger -m "github.com/mjb141/daggerverse/sem-rel@main" call with-config --branch "testbranch" release --dir . --provider "github" --token env:GH_TOKEN --dry-run=false stdout`

## Temporarily modifying the config file

You can modify the config file within the `with-config` method.

### Branch

Your `.releaserc.json` file may only contain branches for CI workflows (e.g. only `main`). For testing purposes you may want to see what Semantic Release will do on your non-configured branch (e.g. a feature branch).

**This does not modify your `.releaserc.json` configuration file**. A modified copy of the configuration file is created for the duration of the container and discarded on completion.

To add your branch for the duration of the execution:

`dagger -m "github.com/mjb141/daggerverse/sem-rel@main" call with-config --branch "my-branch-name" release --dir . --provider "github" --token env:GH_TOKEN stdout`
