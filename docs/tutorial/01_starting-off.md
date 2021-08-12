# Starting Off With Destination: Sol Galaxy Generation
## Introduction
World-Generation in Destination: Sol has recieved a major overhaul as a part of GSoC 2021! It is now possible customize any of the original world generation features. This tutorial will guide you on how this is done.

### WorldBuilder and How Galaxy Generation Works

Before we start actually writing code, let's discuss a little bit about how the new world generation system works. The WorldBuilder class is the central class to the new Destination: Sol world-gen framework. As a modder, you will not have to modify this class itself, but it is helpful to know how it works.

WorldBuilder is loaded whenever a new world is generating. It searches through the entire module space for classes called Generators. These classes tell Destination: Sol how it should generate the various pieces of the game world. You will create Generators by extending various abstract classes: SolarSystemGenerator, PlanetGenerator, MazeGenerator, and BeltGenerator.

After WorldBuilder loads all the available Generator types, it creates new instances of Generators called SolarSystemGenerators and decides what their positions should be. Then it initiates the build process of each SolarSystemGenerator, which will decide all the details within the SolarSystem.

Let's get started! Move on to the first section to create your own SolarSystemGenerator: [Part 1: SolarSystemGenerators](tutorial/02_solar-system-generators.md)