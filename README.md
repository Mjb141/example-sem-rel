# example-sem-rel

## Flags

`--check-if-ci` can disable the Semantic Release check to determine if it is running on a CI platform.

`--dry-run` allows you to check what Semantic Release will do.

## Usage

**After committing and pushing your changes, do one of the following:**

To test what Semantic Release will do set `--dry-run=true`:

`dagger -m "github.com/mjb141/daggerverse/sem-rel@main" call release --dir . --token env:GH_TOKEN --check-if-ci=false --dry-run=true stdout`

To run a release from local both `--check-if-ci=false` and `--dry-run=false` are required.

`dagger -m "github.com/mjb141/daggerverse/sem-rel@main" call release --dir . --token env:GH_TOKEN --check-if-ci=false --dry-run=false stdout`
