 # Daily Challenge 1

 ## http://www.codewars.com/kata/54bf1c2cd5b56cc47f0007a1/train/javascript

On codewars, the challenge was to count the number of characters in a given string which are:

1) Distinct
2) Case Insensitive
3) Alphanumeric
4) Occurring more than once

The example string sets are: "abcde", "aabbcde", "aabbcdeB", "indivisibility", "Indivisibilities", and "aa11"

The biggest help was this thread from StackOverflow: https://stackoverflow.com/questions/9229645/remove-duplicates-from-javascript-array

The solution I came up with is listed below.

  // The function to count the number of duplicate characters in a string
function duplicateCount(text){

  // Declare arrays which will be used to sort, and the variable which will be returned
  var arr = [];
  var dupArr = [];
  var result;
  
    // Loop through the characters in the "text" parameter
  for (var i = 0; i < text.length; i++) {
     
    var lower = text[i].toLowerCase(); // Declare a variable which is used to pass individual characters & make them all lower case
    
      if (arr.indexOf(lower) < 0) { // Here we take one of every letter that is not a duplicate
        arr.push(lower); // Add the result to arr
        
      } else if (dupArr.indexOf(lower) < 0) { // Here we take one of every letter that is left over from the last if statement
        dupArr.push(lower); // Add the result to dupArr
        
      } else {
      }
  }

result = dupArr.length; // Move our solution to an easily identifiable variable, in case we need to use it in something else

return result; // Fire off the solution
}
