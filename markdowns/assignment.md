# Let's get our hands dirty

Now that you know what a Voronoi Diagram is, let's see what you've got! We have a board where multiple firetrucks can move in four directions (up, down, left, right). By using a Voronoi Diagram, a truck always knows what tiles of the grid it has to cover, because the tiles in its Voronoi site are the tiles it would reach first in case a fire starts.

You have to define, for each tile of the grid, in what Voronoi site it is, relative to the trucks' positions. The trucks move around the map randomly.

We call your function at every game turn and draw the map accordingly. **You don't have to code the game, just fill the Voronoi diagram!**

As a reminder, here is the pseudo-code for the naive Voronoi algorithm:

```csharp
 for each (tile in tiles){
   tile.site = null; // Clear site owner of the point
   for each (site in sites){
     double tempdist = distance(tile,site);
     if (tile.site == null || tempdist < distance(tile, tile.site)) {
      tile.site = site; // Update site owner if it's nearest.
     }
   }
 }
```

@[Did you solve it?]({"stubs": ["tron/voronoi.js"], "layout": "aside", "command": "echo 'CG> open --static-dir /project/target/tron /tron.html'"})


::: Got Stuck? Click here to view a solution for this exercise

```javascript
// Create the Voronoi areas
function fillVoronoi (tiles, players) {
  for(var t in tiles) {
    var tile = tiles[t];
    tile.site = null;
	//Then, for each player we will check if it's the nearest:
    for (s in players){
      var site = players[s];
      var tempdist = distance(tile,site);
      if (tile.site === null || tempdist < distance(tile, tile.site) ){
        tile.site = site; // Update site owner
      }
    }
  }
}

function distance(pointA, pointB) {
  //We return the Manhattan distance, that is coded as:
  var dx = pointA.x - pointB.x;
  var dy = pointA.y - pointB.y;
  return Math.abs(dx) + Math.abs(dy); // Manhattan distance formula  
}

```

:::
