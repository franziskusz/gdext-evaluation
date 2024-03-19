# gdext-evaluation results
The following results are based on the first 7 evaluation test series. The raw data is within the `data/` directory.

## Settings and Setup
The runs were done with the following settings, based on the options of the rust/gdscript benchmark applications:

all:
- `initial wave size: 0`
- `mob spawn intervall`
- `bot player: true`
- `safe mode: true`

| # | mob spawns per second | add calculations | calculate n times per mob per frame |
| --: | -----: | ----- | -----: |
| 1 | 10 | false | - |
| 2 | 10 | true | 1 |
| 3 | 5 | true | 10 |
| 4 | 3 | true | 50 |
| 4b | 3 | true | 50 |
| 5 | 2 | true | 100 |
| 6 | 1 | true | 200 |

Hardware:
- MacBook Pro Retina 13 Inch early 2015
- 2.7 GHz Dual Core Intel Core i5
- 8 GB 1867 MHz DDR3
- 128 GB flash drive

OS:
- macOS 12.4 Monterey

## Results 

### Data derived from the Godot benchmark game applications:

| # | time rust-gds | mobs rust-gds | % gds relative to rust | collisions rust-gds | % max collisions relative to max mobs | Ø FPS rust-gds |
| --: | -----: | -----: | -----: | -----: | -----: | -----: |
| 1 | -8 | -80 | **106.8** | 32.6 | **2.8** | **-7.1** |
| 2 | -10.4 | -104 | **110.4** | 24.2 | **2.4** | **-4.3** |
| 3 | 8.8 | 44 | **94.2** | 39.4 | **5.5** | **6.1** |
| 4 | 31.8 | 95.4 | **74.2** | 13.6 | **5** | **10.5** |
| 4b | 34 | 102 | **72.5** | 8.4 | **3.1** | **9.3** |
| 5 | 34.2 | 68.4 | **69.2** | 7.8 | **5.1** | **12.4** |
| 6 | 41 | 41 | **66.7** | 5.8 | **7.1** | **13.7** |

Notes:
- "% gds relative to rust" means max value of active time/mobs of the gds version relative to rust version (= 100 %) -> lower value = rust > gds
- Difference of collisions and Ø FPS is calculated for the time both runs were active

### Data derived from the process-logger:

| # | Ø CPU % | Ø RAM | Ø VRAM | read bytes | written bytes |
| --: | -----: | -----: | -----: | -----: | -----: |
| 1 | -0.34| -183866.3 | 1647107 | 68180380 | -60620.8|
| 2 | -1.02 | -39181570 | -14471780 | -1508966 | -94208 |
| 3 | -1.12 | -27101320 | -21674250 | -462848 | 519372.8 |
| 4 | -0.57 | 7441138 | -465578700 | -1582694 | 924057.6 |
| 4b | -0.4 | -14342330 | -452340400 | 4151706 | 453836.8 |
| 5 | -2.54 | -47639970 | -485637000 | -143360 | 467763.2 |
| 6 | -3.52 | -17563750 |-44127600 | 1737523 | 335052.8 |

Notes:
- Ø CPU % / Ø RAM / Ø VRAM -> mean value over the active time of both versions.
- read bytes / written bytes -> max value over the active time of both versions.
- All values are the difference of rust-gds:
  - negative numbers -> rust used less system resources than gds
  - positive numbers -> rust used more system resources than gds

