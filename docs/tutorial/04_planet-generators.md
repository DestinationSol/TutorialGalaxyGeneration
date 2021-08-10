# Creating A Custom Planet Using PlanetGenerators

Now, let's add a new java Class to our module. Call it TutorialPlanetGenerator, and have it extend PlanetGenerator. Intellij will ask you to implement a method, and when you do, the class will look like this: 

```java
public class TutorialPlanetGenerator extends PlanetGenerator {

    @Override
    public void build() {
        
    }
}
```

PlanetGenerators and slightly simpler than SolarSystemGenerators in that there is only one method we have to manage, the `build()` method. That said, PlanetGenerators are also more exciting than SolarSystemGenerators, as they affect more concrete objects within the game and have more options. 

To create our Planet, first call `setPlanetConfig(getPlanetConfigDefaultSettings());` to set the PlanetConfig. Next, call `setGroundHeight(getGroundHeightUsingDefault());`, `setAtmosphereHeight(DEFAULT_ATMOSPHERE_HEIGHT);`, and `calculateRadius();` to set up the dimensions of the Planet. 

Now, call `setOrbitSolarSystemSpeed(calculateDefaultPlanetOrbitSpeed());` to set the Planet's orbit speed and `setPlanetRotationSpeed(calculateDefaultPlanetRotationSpeed());` to the Planet's rotation speed. Finally, call `setName("TutorialPlanet");` to name the Planet.

Overall, your class should look like this:

```java
public class TutorialPlanetGenerator extends PlanetGenerator {

    @Override
    public void build() {
        setPlanetConfig(getPlanetConfigDefaultSettings());

        setGroundHeight(getGroundHeightUsingDefault());
        setAtmosphereHeight(DEFAULT_ATMOSPHERE_HEIGHT);
        calculateRadius();

        setOrbitSolarSystemSpeed(calculateDefaultPlanetOrbitSpeed());
        setPlanetRotationSpeed(calculateDefaultPlanetRotationSpeed());
        setName(SolRandom.seededRandomElement(solNames.planets.get(getPlanetConfig().moduleName)));

        instantiatePlanet();
    }
}
```

Any of the previous values could be modified. For example, you could call `setOrbitSolarSystemSpeed(calculateDefaultPlanetOrbitSpeed() * 1.5f);` to multiply the orbit speed by 1.5. 

PlanetGenerator also contains several methods that can be used to modify some of the default values contained in PlanetConfig, such as `modifyCloudDensity()` or `modifyGroundEnemiesDensity` to change the frequency of clouds or turrets, respectively. 

As with SolarSystemGenerators, PlanetGenerators can also be modified more extensively by creating your own Config files. More on that later. 

Let's move on to the next section! [Part 4: Maze Generators](tutorial/05_maze-generators.md)