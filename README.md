# example-sem-rel

## Setup

### Tokens

If your config file contains a plugin such as `@semantic-release/github` or `@semantic-release/gitlab` you will need the required API token (personal access token) in your environment.

It does not matter what the token environment variable is named, only that it is provided with the `--token env:<ENV_NAME_HERE>` argument.

## Usage

### Testing

**After committing and pushing your changes, do one of the following:**

To **test** what Semantic Release will do:

`dagger -m "github.com/mjb141/sem-rel@v2.0.0" call release --token env:GH_TOKEN --dir . stdout`

### Releasing

To **release** a new version from local you must explicitly call the `configure` method with `--dry-run=false`:

`dagger -m "github.com/mjb141/sem-rel@v2.0.0" call configure --dry-run=false release --token env:GH_TOKEN --dir . stdout`

## Temporarily modifying release configuration

You can modify your `.releaserc.json` file with the `configure` method.

### Run Options

- `--dry-run=false` *(Optional, default 'true')* Required to run Semantic Release and create new releases
- `--check-if-ci` *(Optional, default 'false')* Optional ability to check if you're running on a CI server or not.

### Release Options

- `--add-current-branch` *(Optional, default 'false')* Add your current branch to `branches` in `.releaserc.json`. Useful to test what will happen on your current branch before merging to main.

- `--remove-git-provider` *(Optional, default 'false') Remove either `@semantic-release/github` or `@semantic-release/gitlab` from your `plugins` list in `.releaserc.json`. This removes the requirement to provide a token for cases when you cannot.

**This does not modify your `.releaserc.json` configuration file**. A modified copy of the configuration file is created for the duration of the container and discarded on completion.
