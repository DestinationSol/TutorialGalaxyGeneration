# Creating A Custom Maze Using MazeGenerators

To work on a MazeGenerator, we need to add another new java Class to our module. Name the class TutorialMazeGenerator, and have it extend MazeGenerator. Intellij will ask you to implement a method, and when you do, the class will look like this: 

```java
public class TutorialMazeGenerator extends MazeGenerator {
    @Override
    public void build() {
        
    }
}
```

In order to get our Maze up and running, we need to call a couple of methods. First, call `setRadius(calculateDefaultMazeSize());` to set the radius of the maze. Then, call `setMazeConfig(getRandomMazeConfig());` to set the Maze config to one of the default configs. Finally, call `instantiateMaze();` to get the Maze into the game.

The class will look like this:

```java
public class TutorialMazeGenerator extends MazeGenerator {
    @Override
    public void build() {
        setRadius(calculateDefaultMazeSize());
        setMazeConfig(getRandomMazeConfig());

        instantiateMaze();
    }
}
```

Now, the game will sometimes generate Mazes using your class. However, these Mazes will be indistinguishable from the game's default Mazes. There are a few ways to modify the Maze. You can multiply the radius by some factor to make the Maze bigger or smaller. You could call one of the methods of MazeGenerator like `modifyBossFrequency();` to change the number of enemies in the Maze. Finally, you can create your own MazeConfig file to modify the Maze more significantly, as we will discuss later.

Let's go on to Belts! [Part 5: BeltGenerators](tutorial/06_belt-generators.md)