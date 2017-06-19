Today's challenge is to find the integer which appears in an array of integers an odd number of times. Examples of test arrays are:

The biggest challenge in this piece of code was to remember that there is a "%" function to give the remainder. A quick web search fixed that issue. My code is as follows:

      // Initialize our function
    function findOdd(A) {
    
        // Set up our variable to deliver the result
      var result;
      
        // Loop through the integers in the array A
      for (var z = 0; z<A.length; z++) {
      
            // Set up our two dimensional array to record the rows of different integers and columns of their repeats
          var arr = [], i;
          
              // Iterate through the new array to make sure that it is populated
            for(i = 0; i < A.length; i++)
                if (A[i] === A[z])
                    arr.push(i);
            
              // Check to see if the remainder of dividing the number of the same integer is equal to 1 
              // (check to see if there are an odd number of the integer)
            if(arr.length%2===1)
            {
                  // If so, then kick out the result and break!
                result=A[z];
                break;
            }
      }
      
        // Done!
      return result;
    }
