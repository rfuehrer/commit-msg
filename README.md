# commit-msg


## Installation

1. ```brew install pre-commit```
2. change to repository
3. create and configure .pre-commit-config.yaml (see below)
4. create and configure .commit-msg-config.yaml (see below)
5. run ```pre-commit install```
6. run ```pre-commit install --hook-type commit.msg```
7. edit .git/hooks/commit-msg (see below)
8. check configuration with ```.git/hooks/commit-msg .commit-msg-config.yaml```

## Configuration

### ./.pre-commit-config.yaml



### ./.commit-msg-config.yaml

```
repos:
-   repo: https://github.com/rfuehrer/commit-msg
    rev: v1.02
    hooks:
    -   id: vkeycheck
```

### .git/hooks/commit-msg

```
...
CONFIG = '.commit-msg-config.yaml'
HOOK_TYPE = 'commit-msg'
...
# end templated
...
```

## Execution