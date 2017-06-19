Today's challenge is as follows:

"If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.
Finish the solution so that it returns the sum of all the multiples of 3 or 5 below the number passed in."

This was a good reminder to use the new arrow function with reduce & to use the modulo operations to make my life easier. Here is how I solved the challenge:

      // Initialize the function
    function solution(number){
    
        // Declare my end variable "result" as an array. This allowed for testing the modulo operations more easily.
      var result = [];
      
        // Loop through the numbers
      for (var i = 0; i < number; i++) {
      
          // Check to see what is divisible by either 3 or 5
        if (i%3==0 || i%5==0) {
        
            // Add that to my array
          result.push(i);
        } 
      }
      
        // Now I'm going to add everything in my array back together
      result = result.reduce((a, b) => a + b, 0);
      
        // Done!
      return result;
    }
