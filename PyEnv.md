## Install
- Xcode install
- install using brew or build from source
```
$ brew install PyEnv
```
- set PATH with 3 commands 

```
$ python -V // python version
$ pyenv install <version> // installs particular version
$ pyenv global <version> // set global version
$ pyenv local <version> // set local version, creates a .py 
$ pyenv versions // lists all versions currently installed
$ pyenv which // shows path to executable for the current python version
$ pyenv help // list of available commands
$ pyenv shell // sets local version for current shell session
$ pyenv uninstall // to uninstall version
$ pyenv install -l // list versions to install
$ pyenv install —list
```

## Virtual Environments
```
$ python -m venv .venv
$ ls .venv/bin
$ source .venv/bin/activate // you’ll see env in shell
```
