In today's challenge, I was tasked with the following:

"You have function one_two that returns 1 or 2 with 50% chance. one_two is already defined in a global scope and can be called everywhere). Your goal is to create function one_two_three that returns 1, 2 or 3 with equal probability using only one_two function. Do not try to cheat returning repeating non-random sequences. There is randomness test especially for this case."

I ended up deciding to use a probability distribution to perform the math function, which is described below:

      // Initialize our function
    function one_two_three() {

        // Collect 2 different answers from the 50/50 function
      var randoTwo = one_two();
      var randoThree = one_two();
  
        // Here we set a loop. This is just in case (just greater than 1/4 chance) the probability distribution has to repeat.
      for (var i = 0; i < 100; i++) {
      
         // Collect 2 different answers from the 50/50 function
      var randoTwo = one_two();
      var randoThree = one_two();
      
          // First coin flip is heads!
        if(randoTwo == 1) {
        
            // Second coin flip is heads!
          if (randoThree == 1) {
            return 1;
            break;
            
            // Second coin flip is tails!
          } else if (randoThree == 2) {
            return 2;
            break;
          }
          
          // First coin flip is tails!
        } else if (randoTwo == 2) {
        
            // Second coin flip is heads!
          if (randoThree == 1) {
            return 3;
            break;
            
            // Second coin flip is tails! Repeat the tree.
          } else if (randoThree == 2) {
        
          }}}}
