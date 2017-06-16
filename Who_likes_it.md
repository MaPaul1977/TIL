Today's challenge is as follows: "Implement a function likes :: [String] -> String, which must take in input array, containing the names of people who like an item. It must return the display text as shown in the examples."

The examples are:

likes [] // must be "no one likes this"
likes ["Peter"] // must be "Peter likes this"
likes ["Jacob", "Alex"] // must be "Jacob and Alex like this"
likes ["Max", "John", "Mark"] // must be "Max, John and Mark like this"
likes ["Alex", "Jacob", "Mark", "Max"] // must be "Alex, Jacob and 2 others like this"

I was having trouble interacting with the "names" variable in a succing way. (I was using a lot of if...else statements.) I was poking around and found: https://github.com/Dirtier/Codewars-JS/blob/master/likes.js

This author inspired my solution below:

      // This function will tell me how many people "like" an item, along with some of their names.
    function likes(names) {
      // Declare a variable to handle cases of 4 or more likes
      var counter = names.length - 2;
    
        // More efficient version of an "if" statement.
      switch(names.length) {
      
        case 0: return "no one likes this"; break; // With 0 likes, give this string
        case 1: return names[0] + " likes this"; break; // With 1 like, give this string
        case 2: return names[0] + " and " + names[1] + " like this"; break; // With 2 likes, give this string
        case 3: return names[0] + ", " + names[1] + " and " + names[2] + " like this"; break; // With 3 likes, give this string
      }
      
      // Handle cases of 4 or more likes
      if (names.length > 3) {
          // Return a string with name, name, and however many other people like this
        return names[0] + ", " + names[1] + " and " + counter + " others like this";
      }
    
    }
