# gdext-evaluation
Overview Repository for a project to evaluate the Rust bindings for the Godot Engine (gdext)

This repository contains no source code but:
- An explanation of the idea and the method of the evaluation project.
- Links to the four repositories containing the programs/scripts created for this purpose.
- [Raw data](data/) collected during the first test series.
- [Plots](plots.md) and [statistics](results.md) created on the basis of the raw data.

The evaluation project consists of five Repositories:

- [this](https://github.com/franziskusz/gdext-evaluation)
- [Godot Rust benchmark game](https://github.com/franziskusz/dodge-r)
- [Godot GDScript benchmark game](https://github.com/franziskusz/dodge-gds)
- [process-logger](https://github.com/franziskusz/process-logger)
- [pandas-plotter](https://github.com/franziskusz/pandas-plotter)


## Idea
Combining the open source game engine [Godot](https://godotengine.org) with the performant language [Rust](https://www.rust-lang.org) seems like a good fit.
Since the bindings are still in development and with not too many finished projects available, the questions of why, where and how to use Rust within Godot are regularly asked.
From the [discord server](https://discord.gg/aKUCJ8rJsc) it can be learned, that GDScript might be more performant when it comes to frequent calls to the engine, while Rust might be more performant, when it comes to actual calculations.
However, actual numbers are rare and opinions on how to benchmark game applications differ.

The main idea was to create two versions of the Dodge-the-Creeps game that are suitable for benchmarking. 
Therefore different optional possibilities to scale and adjust the workload were implemented:
 - Spawn an initial mob wave.
 - Spawn mobs over time.
 - Adjust the spawn intervall.
 - Add additional calculating and drawing tasks per mob per frame.
 - Scale the number of calculations.
 - Make the player character auto move to constantly trigger the targeting function of the mobs.

The [GDScript Version](https://github.com/franziskusz/dodge-gdscript) is besides some minor differences functionally and structurally an 1:1 copy of the [Rust Version](https://github.com/franziskusz/dodge-r), but in pure GDScript.

As a result there are now two versions of basically the same game or benchmark application – one in pure Rust, one in pure GDScript – where the amount of engine calls and the amount of performance intensive calculations and thus their relation to each other can be adjusted arbitrarily.

Both applications write performance logs to timestamped .csv files within the `/app_userdata/` folder. See [godot file paths](https://docs.godotengine.org/en/stable/tutorials/io/data_paths.html) for details.

## How to evaluate
### The easy way
1. Set up and export one or both benchmark game applications
2. Experiment with the settings and just watch the in-game time, mob and fps counters.

### The difficult way
The whole evaluation process:
1. Set up and export both benchmark game applications.
2. Chose scaling settings that suit your need or interest.
3. Start the process-logger entering the the name of process you wish to start with (DodgeR or DodgeGDS for this purpose).
4. Start the corresponding Dodge Version.
5. Run it with the chosen settings for the desired time or until it shuts down because of the fps limit.
6. Stop the process logger.
7. Repeat 3-6 as many times as you want to get average values.
8. Repeat 3-7 for the other Dodge Version.
9. Collect the .csv results in four separate folders (eg. /dodge-r-godot/, /dodge-r-process/, /dodge-gds-godot/, /dodge-gds-process/).
10. Invoke the python pandas script with the four folders as arguments to calculate the arithmetic mean and plot it as well as the difference.
