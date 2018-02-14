## PerlinNoiseComponent

This `PerlinNoiseComponent` is an abstraction layer of [libnoise](http://libnoise.sourceforge.net/) to use in Unreal Engine 4. It is compatible with blueprints and properties can be modified in the editor.

More details in my [article about it](http://blog.lianapigeot.com/projects/unreal-engine-generating-underwater-world/).

## Installation

1. Link libnoise to your UE4 project. See my [libnoise-UE4-ready](https://github.com/nialna/libnoise-UE4-ready) repo for installation of libnoise
2. Drop `PerlinNoiseComponent.cpp` and `PerlinNoiseComponent.h` somewhere in your project Source, and regenerate visual studio project files
3. Change the `UNDERWATER_API` name in `PerlinNoiseComponent.h` to whatever your project's API name is.

## Usage

1. Add the `PerlinNoiseComponent` to any actor
2. You can now use it in blueprints/editor to get noise values.

## API

#### Settings

There are getters and setters in the form of `GetMyProperty` / `SetMyProperty` for the following noise properties:

* `float Frequency`
* `float Lacunarity`
* `PerlinNoiseQuality NoiseQuality`
* `int OctaveCount`
* `float Persistence`
* `int Seed`

The settings themselves are private and should only be modified by calling functions and/or changing values in the Unreal editor before running the game.

You can also use `SetOptions` to set all of them at once:

```c++
void SetupOptions(
	float Frequency,
	float Lacunarity,
	qualities::PerlinNoiseQuality NoiseQuality,
	int OctaveCount,
	float Persistence,
	int Seed
);
```

#### GetValue

To get a noise value, you need to call `GetValue`:

```c++
float GetValue(float x, float y, float z) const;
```

It takes the x,y,z coordinates as input, and returns a noise value (that should be between -1 and 1) as an output

**Warning:** The noise functions don't work with integer values. If you give integer properties (even floats with no decimals) it will always return 0. A simple way to avoid this is to add some number like 0.1 to your `GetValue` calls if the input coordinates you're using are whole numbers.