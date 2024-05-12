# yoorie; Macros

## Clone the repository

```
cd ~/printer_data/config
git clone https://github.com/flaming-moe/klipper-macros.git yoorie-macros
```

## Add moonraker update definition (moonraker.conf)

```
[update_manager yoorie-macros]
type: git_repo
path: ~/klipper-macros
origin: https://github.com/flaming-moe/klipper-macros.git
primary_branch: main
managed_services: klipper
```