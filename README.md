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