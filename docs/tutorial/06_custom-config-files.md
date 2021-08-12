# Using Custom Config Files In Generators

It is possible to use custom config files to modify Generators extensively. For example, let's take a look at one of the default PlanetConfig's JSON data: 

```json
 "rocky": {
        "easyOnly": true,
        "minGrav": 0.4,
        "maxGrav": 0.6,
        "groundTexs": "core:rockyGround",
        "cloudTexs": "core:cloud",
        "rowCount": 4,
        "smoothLandscape": true,

        "sky": {
            "dawnColor": "hsb 0 50 100",
            "dayColor": "hsb 216 40 100"
        },

        "decorations": {
            "core:rockyDecorationGrass": {
                "density": 0.3,
                "szMin": 0.1,
                "szMax": 0.2,
                "orig": "0 0.5",
                "allowFlip": true
            },

            "core:rockyDecorationTree": {
                "density": 0.4,
                "szMin": 0.7,
                "szMax": 0.8,
                "orig": "0 0.5",
                "allowFlip": true
            }
        },

        "highOrbitEnemies": [
            {
                "hull": "core:pirateOrbiter",
                "items": "core:plasmaGun+core:blaster 0.24|core:smallShield",
                "money": 40,
                "density": 0.03
            }
        ],

        "lowOrbitEnemies": [
            {
                "hull": "core:pirateOrbiter",
                "items": "core:bombGun 0.24|core:smallShield",
                "money": 50,
                "density": 0.1
            }
        ],

        "groundEnemies": [
            {
                "hull": "core:piratePlanetTurret",
                "items": "core:plasmaGun+core:blaster 0.36|core:smallShield",
                "money": 110,
                "density": 0.45
            },

            {
                "hull": "core:pirateSmall",
                "items": "core:blaster+core:gun 0.5|core:smallShield+core:shield",
                "money": 60,
                "density": 0.15
            }
        ],

        "station": {
            "hull": "core:drome",
            "items": "core:gun+core:shotGun core:shield 4*rep"
        },

        "trading": {
            "items": "rep core:plasmaClip core:shotGun core:shellClip core:mineClip core:bombGun core:bombClip core:missileClip core:shield core:unShieldCharge",
            "ships": "core:pirateSmall core:pirateOrbiter core:pirateMedium",

            "mercenaries": [
                {
                    "hull": "core:pirateSmall",
                    "items": "core:blaster+core:gun core:smallShield 3*rep",
                    "money": 100
                }
            ]
        }
    }
```

We can see from this file that there are many details to Planets (and other features as well) that can be set by the config data. In order to create your own preset configs, all you need to do is copy an existing config and change whichever values you wish to change. Then, you need to load the config using the `load()` method of the appropriate config manager. For example, if I want to load a custom PlanetConfig, I will call `getConfigManager().load()` in my PlanetGenerator class. The parameters to the `load()` method should be the name of your JSON file and the default schema from the engine (for example, "engine:schemaPlanetsConfig" for Planets).
