Today's challenge was to take a ten minute walk. Here are the parameters:

"You live in the city of Cartesia where all roads are laid out in a perfect grid. You arrived ten minutes too early to an appointment, so you decided to take the opportunity to go for a short walk. The city provides its citizens with a Walk Generating App on their phones -- everytime you press the button it sends you an array of one-letter strings representing directions to walk (eg. ['n', 's', 'w', 'e']). You know it takes you one minute to traverse one city block, so create a function that will return true if the walk the app gives you will take you exactly ten minutes (you don't want to be early or late!) and will, of course, return you to your starting point. Return false otherwise.

Note: you will always receive a valid array containing a random assortment of direction letters ('n', 's', 'e', or 'w' only). It will never give you an empty array (that's not a walk, that's standing still!)."

In order to solve, I just created an x, y axis:

      // Initialize the function
    function isValidWalk(walk) {
  
        // y will represent our north-south axis
      var y = 0;
        // x will represent our east-west axis
      var x = 0;

        // Loop through the walk array
      for (var i = 0; i<walk.length; i++) {
  
           // North
         if (walk[i] == 'n') {
           y++;
      
          // South
        } else if (walk[i] == 's') {
          y--;
      
          // West
        } else if (walk[i] == 'w') {
           x++;
      
          // East
         } else if (walk[i] == 'e') {
          x--;
        }
       }
  
          // We must be back at start, and take exactly 10 minutes to do so
       if (y == 0 && x == 0 && walk.length == 10) {
        return true;
      } else {
        return false;
      } 
    }
