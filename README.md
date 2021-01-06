[dotbot_repo]: https://github.com/anishathalye/dotbot
[aptget_repo]: https://github.com/dein0s/dotbot_plugin_aptget

## Dotbot ```sudo``` Plugin

Plugin for [Dotbot][dotbot_repo], that adds ```sudo``` directive, which allows you to run given direcives as root user. 

## Installation

1. Simply add this repo as a submodule of your dotfiles repository:
```
git submodule add https://github.com/68696c6c/dotbot-sudo.git
```

2. Pass the path to the sudo.py file with corresponding flag to your [Dotbot][dotbot_repo] script:
  - ```-p /path/to/file/sudo.py```

## Supported task variants
```yaml
...
- sudo: 
    - other_directive: # like in the root of the config file
   ...
```

## Usage

### Example config
```yaml
...
- sudo:
    - clean: ['/root']
    - aptget: [package_name_one, package_name_two, package_name_three]
    ...
...
```

### Execution
Edit your `install` script to add the plugin:
```bash
"${BASEDIR}/${DOTBOT_DIR}/${DOTBOT_BIN}" -d "${BASEDIR}" -c "${CONFIG}" -p "${BASEDIR}/dotbot-sudo/sudo.py" "${@}"
```

Using absolute paths instead of vars would look something like this:
```bash
"~/.dotfiles/bin/dotbot" -d "~/.dotfiles" -c "~/.dotfiles/install.conf.yaml" -p "~/.dotfiles/dotbot-sudo/sudo.py" "${@}"
```

