# Creating A Custom Solar System using SolarSystemGenerators

This section of the tutorial will guide you in creating you own type of SolarSystem using SolarSystemGenerators.

First, create a new module for your tutorial work. A guide to creating and working with modules can be found at [https://github.com/MovingBlocks/DestinationSol/wiki/Initializing-a-Module](https://github.com/MovingBlocks/DestinationSol/wiki/Initializing-a-Module).

It is best to name your module a different name than this tutorial module, otherwise the game engine might use this one by mistake.

Once you've got the module set up, you should add a new Java class to it called TutorialSolarSystemGenerator. This class should extend SolarSystemGenerator. When you extend the class, you will be prompted to add three methods. Press 'implement methods' and it will look like this:

```java
public class TutorialSolarSystemGenerator extends SolarSystemGenerator {
    @Override
    public SolarSystem build() {
        return null;
    }

    @Override
    public SolarSystemSize getSolarSystemSize() {
        return null;
    }

    @Override
    public int getCustomFeaturesCount() {
        return 0;
    }
}
```

Here, you see three methods that we will need to modify to create our SolarSystem. Build() is where you will do most of your modification. getSolarSystemSize() is where you will decide what size you SolarSystem should be. You can set the return value to be either SMALL, MEDIUM, or LARGE. You can ignore the third method for now. 

To start off, let's set the SolarSystem size. Let's choose MEDIUM. The method should look like this:

```java
@Override
public SolarSystemSize getSolarSystemSize() {
    return SolarSystemSize.MEDIUM;
}
```

Now, let's move on to the build() method. There are several methods we need to call from build() to ensure that the SolarSystem loads correctly. First, call `getSolarSystemConfigManager().loadDefaultSolarSystemConfigs();`. This ensures that the game has access to the default SolarSystemConfig classes. Next, lets set the config for our SolarSystem. Call `setSolarSystemConfigUsingDefault();` to set a default config for our SolarSystemGenerator.

After setting config info, we will add calls for choosing a name and setting up features. Call `setName("TutorialSystem");` to name the system. Then, call `initializeRandomDefaultFeatureGenerators(1f);` to initialize random types of features (Planets, Mazes, Belts, etc.) to populate our SolarSystem. Finally, call `calculateFeaturePositions();` and `buildFeatureGenerators();` to place and build those features within our System. 

To have the SolarSystem actually spawn in the world, we need to have `build()` return an object of type SolarSystem. Therefore, finish up the method by calling `return createInstantiatedSolarSystem();`. Now, when you play the game, you will come across SolarSystems named 'TutorialSystem' with the properties we determined.

At this point, the `build()` method looks like this: 
```java
@Override
    public SolarSystem build() {
        getSolarSystemConfigManager().loadDefaultSolarSystemConfigs();
        setSolarSystemConfigUsingDefault();

        setName("TutorialSystem");
        initializeRandomDefaultFeatureGenerators(1f);
        calculateFeaturePositions();
        buildFeatureGenerators();
        
        return createInstantiatedSolarSystem();
    }
```

If you want to get creative, you can try changing the size by having `getSolarSystemSize()` return `SolarSystemSize.LARGE` or `SolarSystemSize.SMALL`. You can also create your own SolarSystemConfig to change more properties of SolarSystems, like which enemies spawn in them. More on that later. 

Let's move on to the next section: [Part 2: PlanetGenerators](tutorial/03_planet-generators.md)
 

