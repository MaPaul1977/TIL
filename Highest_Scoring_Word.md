Today's challenge was:

"Given a string of words (x), you need to find the highest scoring word. Each letter of a word scores points according to it's position in the alphabet. a=1, z=26 and everything inbetween. You need to return the highest scoring word as a string.

If two words score the same, return the word that appears earliest in the original string.

All letters will be lower case and all inputs will be valid."

I solved it through a little bit of a competition. Theoretically this could work for any tournament system to find just the winner:

      // Initialize the function
    function high(x){
    
      // Set up the alphabet which I will use to set up alphaCheck
    var alphabet = []
    alphabet = 'abcdefghijklmnopqrstuvwxyz'.split('');
    
       // Set up alphaCheck to score the words
    var alphaCheck = [];
    
       // Give each letter a score
    for (var i = 0; i < alphabet.length; i++) {
    	alphaCheck.push([alphabet[i], i]);
    }
    
      // Make the word list usable
    var wordList = x.split(' ');
    
      // Set up the array to handle each word
    var word = [];
    
      // Declare the array which will hold the winner
    var winner = ['', 0];
    
      // Declare the array which will hold our contender
    var contender = [];
    
      // Set up our scoring system
    var score;
    
      // Cycle through our words to make them lowercase
    for (var i = 0; i < wordList.length; i++) {
    	wordList[i] = wordList[i].toLowerCase();
     }
    
      // Cycle through each word
    for (var i = 0; i < wordList.length; i++) {
    
        // Split apart the letters of each word
    	word = wordList[i].split('');
      
        // There are no free lunches!
      score = 0;
      
        // Let us loop through the letter of each word to see how they stack up to our scoring mechanism
      for (var j = 0; j < word.length; j++){
      	for (var k = 0; k < alphaCheck.length; k++) {
       	
            // For each letter, give the word a cumulative score
        	if (word[j] == alphaCheck[k][0]) {
          	score += alphaCheck[k][1];
          }
        }
      }
      
        // Set up our contender!
      contender = [wordList[i], score];
      
        // Can the contender beat our current winner?
      if (contender[1] > winner[1]){
      
          // If so, then the contender is now the winner!
        winner = contender;
      }
    }
    
      // And we have found our champion
    return winner[0];
    }
