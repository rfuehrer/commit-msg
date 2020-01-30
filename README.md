# commit-msg

commit-msg is a repository for pre-commit hooks, which are designed for the 'commit-msg' hook. Its purpose is to check commit messages before committing, to ensure that certain content must or may not be specified in the commit message. This last aspect in particular plays an important role in the enterprise environment with regard to IT security and data protection.

The goal of this repository is to make it easy to set up the hooks using the existing scripts and to make it easy to customize for user repositories.

The use is described using two approaches: Use as a bash script alone and use as a module of ```pre-commit``` (a Python module). Since it makes sense to have different checks, this description focuses on the integration into ```pre-commit```. The manual way is also indicated.

## Installation

# Manual integration

In order to use the hook in its current form, the only important file is ./.github/hooks/pre-commit. This file is available in this repository as a bash script and can be used on systems that can execute bash script. Please note that the file currently only executes one function and that you may need to add further checks in your local copy. Please also note that existing files may be overwritten.

## Installation

1. clone repository
2. ```chmod +x ./.guthub/hooks/pre-commit````

# Python module 'pre-commit' integration
  
In addition to the Python module `pre-commit`, the installation uses its own configuration via the new file `commit-msg-config.yaml`, where own hooks can be used in contrast to `pre-commit-config.yaml`. Since not all checks are required in a commit message, this can reduce complexity and error-proneness and increase the speed of the check.  

The installation requires the adaptation of the script installed by pre-commit. It should be noted that any update and installation can reset this script, overwriting the customizations. In this case, all hooks will be executed again, which may result in the desired hooks not being executed. It is therefore important to make sure that this script is only overwritten in a controlled manner and is adjusted again if necessary (see below).  

## Installation  

1. ```brew install pre-commit```
2. change to repository
3. create and configure `.pre-commit-config.yaml` (see below)
4. create and configure `.commit-msg-config.yaml` (see below)
5. run `pre-commit install`
6. run `pre-commit install --hook-type commit.msg`
7. edit .git/hooks/commit-msg (see below)
8. check configuration with `.git/hooks/commit-msg .commit-msg-config.yaml`

Notice:  
The repository must still use the .pre-commit-hooks.yaml file in the root directory, despite a different hook. This is due to the ```pre-commit``` script, which is not adapted here. However, since this is only necessary on the server side, it can be left as it is without local customization.  

## Configuration. 

### ./.pre-commit-config.yaml 

tba

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
