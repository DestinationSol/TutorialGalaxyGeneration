# WorldBuilder and How Galaxy Generation Works

The WorldBuilder class is the central class to the new Destination: Sol world-gen framework. As a modder, you will not have to modify this class itself, but it is helpful to know how it works.

WorldBuilder is loaded whenever a new world is generating. It searches through the entire codebase for classes called Generators. These classes tell Destination: Sol how it should generate the various pieces of the game world.

After WorldBuilder loads all the available Generator types, it creates new instances of Generators called SolarSystemGenerators and decides what their positions should be. Then it initiates the build process of each SolarSystemGenerator, which will decide all the details within the SolarSystem.

Move on to the next section to learn how to create your own SolarSystemGenerator: [Part 2: SolarSystemGenerators](tutorial/03_solar-system-generators.md)