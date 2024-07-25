# example-sem-rel

## Usage

To run a release from local both `--check-if-ci=false` and `--dry-run=false` are required.

`dagger -m "github.com/mjb141/daggerverse/sem-rel@sem-rel" call release --dir . --token env:GH_TOKEN --check-if-ci=false --dry-run=false stdout`

To test what Semantic Release will do removing `--dry-run=false` is sufficient.

`dagger -m "github.com/mjb141/daggerverse/sem-rel@sem-rel" call release --dir . --token env:GH_TOKEN --check-if-ci=false stdout`
