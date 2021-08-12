# Creating A Custom Asteroid Belt Using Belt Generators

BeltGenerators allow us to work on another aspect of the Destination: Sol world. Let's get started by making a new class called TutorialBeltGenerator in our module. It should extend BeltGenerator. It will start off like this:

```java
public class TutorialBeltGenerator extends BeltGenerator {
    @Override
    public void build() {
        
    }
}
```

In order to get our Belt up and running, we need to call a couple of methods. First, call `setRadius(DEFAULT_BELT_HALF_WIDTH);` to set the radius of the Belt. Then, call `setBeltConfig(getBeltConfigManager().getRandomBeltConfig(getIsInFirstSolarSystem()));` to set the Belt config to one of the default configs. Finally, call `instantiateSystemBelt();;` to get the Belt into the game.

The class will look like this:

```java
public class TutorialBeltGenerator extends BeltGenerator {
    @Override
    public void build() {
        setRadius(DEFAULT_BELT_HALF_WIDTH);
        setBeltConfig(getBeltConfigManager().getRandomBeltConfig(getIsInFirstSolarSystem()));

        instantiateSystemBelt();
    }
}
```

Now, the game will sometimes generate Belts using your class. However, these Belts will be indistinguishable from the game's default Belts. There are a few ways to modify the Belt. You can multiply the radius by some value to make the belt wider or narrower. You could also call, for example, `modifyBeltAsteroidFrequency(1.2f);` to multiply the frequency of asteroids in the belt by 1.2. Finally, you can create your own BeltConfig file to modify the Belt more significantly, as will discuss in the next section.

Let's move on to [Part 5: Custom Config Files](tutorial/06_custom-config-files.md)

