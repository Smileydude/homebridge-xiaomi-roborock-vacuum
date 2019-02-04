# Homebridge-xiaomi-roborock-vacuum

[![PayPal Donate](https://img.shields.io/badge/PayPal-Donate-blue.svg)](https://www.paypal.me/smileydude)
[![GitHub last commit](https://img.shields.io/github/last-commit/smileydude/homebridge-xiaomi-roborock-vacuum.svg)](https://github.com/smileydude/homebridge-xiaomi-roborock-vacuum)
[![npm](https://img.shields.io/npm/dt/homebridge-xiaomi-roborock-vacuum-zones.svg)](https://www.npmjs.com/package/homebridge-xiaomi-roborock-vacuum-zones)
[![npm version](https://badge.fury.io/js/homebridge-xiaomi-roborock-vacuum-zones.svg)](https://badge.fury.io/js/homebridge-xiaomi-roborock-vacuum-zones)
[![dependencies Status](https://david-dm.org/smileydude/homebridge-xiaomi-roborock-vacuum.svg)](https://david-dm.org/smileydude/homebridge-xiaomi-roborock-vacuum.svg)

## Config Overview

Currently you need to replicate the config for each room, and just change the zones coordinates. You can get the coordinates by either trial and error, then checking the map after sending it off or send it off and and take a screen shot of the zone. Print it out and figure out the scale, and calculate all the zones.

The dock is around the middle [25600, 25600], the whole map can get as big as 51200 x 51200. Mine is no where near that. The coordinate order is [bottom-left-x, bottom-left-y, top-right-x, top-right-y]

For Xiaomi roborock v2 you can save your map, this will prevent it from getting rotated. Make sure to do one cleanup and then save the map! You will not need the all zone config (House Vacuum in example) as it can still do a default cleanup now without rotating the map. Just remove the zones part of config and it will do a normal cleanup (I still prefer one as I think it does a better job when you tell it what the outline of the room is)

For Xiaomi roborock v1 you are going to need a zone that has a list of all your zones. i.e. Like the house vacuum in the example. If you omit the zones config here it will do all the space, but as one big room. It does the worst job and takes forever.
**If your map gets screwed up because it got stuck or you picked it up, just keep starting new full cleanups till it matches again should rotate by 90 degrees each time**

You can add in an extra number to a zone for the amount of times you want it to do a single area. 

```json
"accessories": [
    {
            "accessory": "XiaomiRoborockVacuum",
            "name": "Bathroom Vacuum Running Twice",
            "ip": "ip",
            "token": "token",
            "dock": false,
            "pause": false,
            "zones": [
                [
                    23000,
                    26900,
                    26000,
                    29000,
                    2
                ]
            ]
        }
    ]
```

#### Example

<img src="https://github.com/Smileydude/homebridge-xiaomi-roborock-vacuum/blob/master/example.PNG?raw=true" alt="Layout example" width="650">

```json
"accessories": [
    {
            "accessory": "XiaomiRoborockVacuum",
            "name": "Bathroom Vacuum",
            "ip": "ip",
            "token": "token",
            "dock": false,
            "pause": false,
            "zones": [
                [
                    23000,
                    26900,
                    26000,
                    29000
                ]
            ]
        },
        {
            "accessory": "XiaomiRoborockVacuum",
            "name": "Kitchen Vacuum",
            "ip": "ip",
            "token": "token",
            "dock": false,
            "pause": false,
            "zones": [
                [
                    20010,
                    28200,
                    22035,
                    29955
                ],
                [
                    22090,
                    27160,
                    23325,
                    32035
                ]
            ]
        },
        {
            "accessory": "XiaomiRoborockVacuum",
            "name": "Bedroom Vacuum",
            "ip": "ip",
            "token": "token",
            "dock": false,
            "pause": false,
            "zones": [
                [
                    23000,
                    22285,
                    26000,
                    26910
                ]
            ]
        },
        {
            "accessory": "XiaomiRoborockVacuum",
            "name": "Living Room Vacuum",
            "ip": "ip",
            "token": "token",
            "dock": false,
            "pause": false,
            "zones": [
                [
                    19360,
                    22285,
                    23000,
                    27745
                ]
            ]
        },
        {
            "accessory": "XiaomiRoborockVacuum",
            "name": "House Vacuum",
            "ip": "ip",
            "token": "token",
            "dock": false,
            "pause": false,
            "zones": [
                [
                    19360,
                    22285,
                    23000,
                    27745
                ],
                [
                    23000,
                    22285,
                    26000,
                    26910
                ],
                [
                    20010,
                    28200,
                    22035,
                    29955
                ],
                [
                    22090,
                    27160,
                    23325,
                    32035
                ],
                [
                    23000,
                    26900,
                    26000,
                    29000
                ]
            ]
        }
    ]
```

#### Token
There are [many ways](https://github.com/jghaanstra/com.xiaomi-miio/blob/master/docs/obtain_token.md). I followed the none jailbroken iphone way using ibackup viewer

## Optional parameters
| Name of parameter | Default value | Notes |
|---|---|---|
| `pause` | false | when set to true, HomeKit shows an additional switch for "pause" - switch is on, when pause is possible |
| `dock` | false |  when set to true, HomeKit shows an occupancy sensor, if robot is in the charging dock |


## Xiaomi Token
To use this plugin, you have to read the "token" of the xiaomi vacuum robots. Here are some detailed instructions:
- :us::gb: - [python-miio - Getting started](https://python-miio.readthedocs.io/en/latest/discovery.html)
- :de: - [Apple HomeKit Forum - HomeKit.Community](https://forum.smartapfel.de/forum/thread/370-xiaomi-token-auslesen/)
- :de: - [Homematic-Guru.de](https://homematic-guru.de/xiaomi-vacuum-staubsauger-roboter-mit-homematic-steuern)

## Lisense
The MIT License (MIT)

Copyright (c) 2018 Smileydude

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
