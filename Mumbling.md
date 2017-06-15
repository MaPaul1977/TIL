 # Daily Challenge 2

 ## https://www.codewars.com/kata/mumbling/train/javascript

On codewars, the challenge was to convert a given string of upper and lowercase letters into a string of the same letters in uppercase with an increasing number of lowercase letters after each uppercase letter. Example:

accum("abcd");    // "A-Bb-Ccc-Dddd"
accum("RqaEzty"); // "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
accum("cwAt");    // "C-Ww-Aaa-Tttt"

I used a StackOverflow threat to find the repeat(); functionality:

  https://stackoverflow.com/questions/1877475/repeat-character-n-times

The solution I came up with is listed below:


      // This is the function which will make the conversion described above.
    function accum(s) {
    
	    // Declare variables to create two arrays based on the string s
      var upper = s.toUpperCase().split(""); // This makes an array of uppercase letters from string s
      var lower = s.toLowerCase().split(""); // This makes an array of lowercase letters from string s
      var arr = []; // This prepares my array variable to receive
      var result; // I like delivering my return in an easily identifiable "result" variable
      
        // Loop through the letters in the string s
      for (var i = 0; i < s.length; i++) {
      
        // Add an uppercase letter, and the number of lowercase letters equal to the index of the current letter
       arr.push(upper[i] + lower[i].repeat(i));
       
      } 
      
        // Concantenate the objects in my array with a hyphen. This will satisfy the requirements of the exercise.
      result = arr.join("-");
      
        // Done!
      return result;
      
    }
