# yoorie; Macros

These are macros that I use for my self-built printers. These macros require that variables can be saved. This can be achieved with this entry in printer.cfg.

```
[save_variables]
filename: ~/printer_data/config/variables.cfg
```

For setting needed constants you may add also a delayed macro to initilize them.
e.g.

```
[delayed_gcode my_initialization]
initial_duration: 1
gcode:
  INITIALIZE_VARIABLE VARIABLE=park_x VALUE=105
  INITIALIZE_VARIABLE VARIABLE=park_y VALUE=210
  INITIALIZE_VARIABLE VARIABLE=bowden_len VALUE=70
  INITIALIZE_VARIABLE VARIABLE=filament_load_distance VALUE=70
  INITIALIZE_VARIABLE VARIABLE=filament_purge_distance VALUE=25
  INITIALIZE_VARIABLE VARIABLE=filament_sensor_name VALUE="\"encoder_sensor\""
  INITIALIZE_VARIABLE VARIABLE=switch_sensor_name VALUE="\"switch_sensor\""
  SET_FILAMENT_SENSOR SENSOR=switch_sensor ENABLE=0
  SET_FILAMENT_SENSOR SENSOR=encoder_sensor ENABLE=0
```
If I can manage it, I will create a list of setting variables later.

## Clone the repository

```
cd ~/printer_data/config
git clone https://github.com/flaming-moe/klipper-macros.git yoorie-macros
```

## Include macros in printer.config

```
[include yoorie-macros/*.cfg]
```
This should be inserted after [include mainsail.cfg] and before your own macros. So you are able to overwrite e.g. the CANCEL_PRINT macro. 


## Add moonraker update definition (moonraker.conf)

```
[update_manager yoorie-macros]
type: git_repo
path: ~/klipper-macros
origin: https://github.com/flaming-moe/klipper-macros.git
primary_branch: main
managed_services: klipper
```

