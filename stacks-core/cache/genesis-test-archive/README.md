# Genesis Test Archive Cache action

[Nextest](https://nexte.st) archive of genesis tests

- `check` - Verifies if the cache already exists
- `restore` - Restores a cache if it exists
- `save` - Saves the [nextest](https://nexte.st) archive

## Documentation

### Inputs

| Input | Description | Required | Default |
| ------------------------------- | ----------------------------------------------------- | ------------------------- | ------------------------- |
| `action` | Type of cache action - one of: `check`, `restore`, `save` | true | `check` |
| `cache-key` | Cache Key name | false | `${{ github.event.repository.name }}-${{ github.sha }}-test-archive` |
| `fail_ci_if_error` | Fail the workflow on an error | false | `false` |
| `retries` | Number of times to retry codecov upload | false | `3` |
| `retry-delay` | Time in ms between upload retries | false | `10000` |

### Outputs

| Output | Description |
| ------------------------------- | ----------------------------------------------------- |
| `cache-hit` | Returns a boolean if a cache is found (_only applicable in the `check` input action_) |

## Usage

### Check Cache

```yaml
name: Action
on: push
jobs:
  foo:
    name: bar
    runs-on: ubuntu-latest
    steps:
      - name: Check Cache
        id: check_cache
        uses: stacks-network/actions/stacks-core/cache/genesis-test-archive@main
```

### Restore Cache

```yaml
name: Action
on: push
jobs:
  foo:
    name: bar
    runs-on: ubuntu-latest
    steps:
      - name: Restore Cache
        id: restore_cache
        uses: stacks-network/actions/stacks-core/cache/genesis-test-archive@main
        with:
          cache-action: restore
```

### Save Cache

```yaml
name: Action
on: push
jobs:
  foo:
    name: bar
    runs-on: ubuntu-latest
    steps:
      - name: Save Cache
        id: save_cache
        uses: stacks-network/actions/stacks-core/cache/genesis-test-archive@main
        with:
          cache-action: save
```
