# FiveM Combined Vehicles Resource

A guide on how to efficiently pack multiple vehicle addons into a single FiveM resource.

## Structure

```
PackedVehicles/
│
├── data/
│   └── toyota_tundra_2011_doublecab/
│       ├── handling.meta
│       ├── vehicles.meta
│       ├── carcols.meta
│       ├── carvariations.meta
│       └── vehiclelayouts.meta
│
├── stream/
│   └── toyota_tundra_2011_doublecab/
│       ├── vehicle.ytf
│       └── vehicle.ytd
│
└── fxmanifest.lua
```

## Setup Instructions

1. Create your base resource folder (e.g., `PackedVehicles`)

2. Inside the base folder, create two folders:
   - `data` (for meta files)
   - `stream` (for stream files)

3. Create a `fxmanifest.lua` in the base folder with the following content:

```lua
-- Resource Metadata
fx_version 'adamant'
game 'gta5'
description ''
author ''

files {
    'data/**/*.meta',
    'data/**/*.xml',
    'data/**/*.dat',
    'data/**/*.ytyp'
}

data_file 'HANDLING_FILE'                   'data/**/handling*.meta'
data_file 'VEHICLE_LAYOUTS_FILE'            'data/**/vehiclelayouts*.meta'
data_file 'VEHICLE_METADATA_FILE'           'data/**/vehicles*.meta'
data_file 'CARCOLS_FILE'                    'data/**/carcols*.meta'
data_file 'VEHICLE_VARIATION_FILE'          'data/**/carvariations*.meta'
data_file 'CONTENT_UNLOCKING_META_FILE'     'data/**/*unlocks.meta'
data_file 'PTFXASSETINFO_FILE'              'data/**/ptfxassetinfo.meta'

-- client_scripts {
--     'vehicle_names.lua',
-- }

-- server_script 'server.lua'
```

## Adding Vehicles

For each vehicle you want to add:

1. Create a folder with the vehicle's name in both `data` and `stream` directories
   - Example: `toyota_tundra_2011_doublecab`

2. Place the vehicle's files in their respective folders:
   - Meta files (`.meta`) go in the `data/vehicle_name/` folder
   - Stream files (`.ytf`, `.ytd`) go in the `stream/vehicle_name/` folder

## Example Vehicle Structure

Using Toyota Tundra 2011 Double Cab as an example:

### Data Files Location
```
data/toyota_tundra_2011_doublecab/
├── handling.meta
├── vehicles.meta
├── carcols.meta
├── carvariations.meta
└── vehiclelayouts.meta
```

### Stream Files Location
```
stream/toyota_tundra_2011_doublecab/
├── vehicle.ytf
└── vehicle.ytd
```

## Notes
- Keep vehicle folder names consistent between `data` and `stream` directories
- Use underscores instead of spaces in folder names
- Make sure all required meta files are present for each vehicle
- The `fxmanifest.lua` configuration handles all nested folders automatically
