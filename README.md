# Colored Lines

Colored Lines is a "Connect Four" look-a-like made with Processing. 

Original Game rules:

* Click a ball, then click an empty square to move.
* You can only move along unblocked paths.
* Build rows of 5 or more balls of one color to score.

Custom features:

* The player can choose between three board sizes (16x20, 8x10 or 4x5).
* The player can choose the number of colors (3, 6 or 9).
* The player to start the game with pre-set occupied squares, by choosing the dificulty (medium or hard).
* The player can choose Android Mode, and use a smartphone as a controller, see more info below.
* The player can choose Color Scanner, use a smartphone camera to scan real life colors (e.g. yellow banana) and use them in-game, see more info below.



![screenshot 1](https://github.com/ricardoreais/colored-lines/blob/master/examples/intro.png "Intro screen")

![screenshot 2](https://github.com/ricardoreais/colored-lines/blob/master/examples/mode1.png "Game mode 1")

[Click here for more  in-game screenshots](https://github.com/ricardoreais/colored-lines/tree/master/examples)

## Code Example

The game main engine is the shortest path selector, which determines the next position of the ball (i.e. the ball path). Checking if the path between the ball and the user click isn't blocked.

```Processing
void shortestPath(int [][] d, int r, int c, int[][] p) //Generate the shortest path possible
{
  int currentDistance = d[r][c];
  while (currentDistance >= 1)
  {
    p[r][c] = 1;
    int direction = -1; //currentDistance direction is -1
    sDistance(d, r, c); //southCell direction is 0
    nDistance(d, r, c); //northCell direction is 1
    eDistance(d, r, c); //eastCell direction is 2
    wDistance(d, r, c); //westCell direction is 3  
    for (int i = 0; i < 4; i++) //Checks the lowest distance available
      if (currentDistance > adjacent[i]  && adjacent[i] >= 0)
      {
        currentDistance = adjacent[i];
        direction = i;
      } 
    if (currentDistance != 0)
    {
      if (direction == -1) //If the lowest distance is the current, stay
        p[r][c] = 1;
      if (direction == 0) //If the lowest distance is south, move south
        p[r++][c] = 1;
      if (direction == 1) //If the lowest distance is north, move north
        p[r--][c] = 1;
      if (direction == 2) //If the lowest distance is east, move east
        p[r][c++] = 1;
      if (direction == 3) //If the lowest distance is west, move west
        p[r][c--] = 1;
    }
  }
}
```

## Getting Started
### Prerequisites

You will need to download processing version 3.x.

[Click here to download Processing](https://processing.org/download/)

### Opening the project

Once you have to Processing editor on the left upper corner, click on File>open...>coloredLines.pde

This will open the game project.

## Running the game

You can run the game by clicking the "Play" button on the processing IDE.

## Deployment

Export the application and make an executable file. On the left upper corner, click on File>Export application...

## Built With

* [Processing 3.3](https://processing.org/download/) - The IDE used.
* [Adobe photoshop](https://www.adobe.com/pt/products/photoshop.html?promoid=KLXLS&mv=search&s_kwcid=AL!3085!3!180232924738!b!!g!!adobe%20photoshop%20gr%C3%A1tis&ef_id=WL7ZFwAAACZ40aWn:20170314164153:s) - The artwork editor.

## API Reference

Depending on the size of the project, if it is small and simple enough the reference docs can be added to the README. For medium size to larger projects it is important to at least provide a link to where the API reference docs live.

## Authors

* **Ricardo Reais** - *Initial work* - [My profile](https://github.com/ricardoreais)

See also the list of [contributors](https://github.com/ricardoreais/colored-lines/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Credits to the [Games for the brain version](https://www.adobe.com/pt/products/photoshop.html?promoid=KLXLS&mv=search&s_kwcid=AL!3085!3!180232924738!b!!g!!adobe%20photoshop%20gr%C3%A1tis&ef_id=WL7ZFwAAACZ40aWn:20170314164153:s)
