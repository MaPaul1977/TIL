Today's challenge is to take a string of bowling frame scores and figure out what the final score would be. The official description is here:

## Ten-Pin Bowling

In the game of ten-pin bowling, a player rolls a bowling ball down a lane to knock over pins. There are ten pins set at the end of the bowling lane. Each player has 10 frames to roll a bowling ball down a lane and knock over as many pins as possible. The first nine frames are ended after two rolls or when the player knocks down all the pins. The last frame a player will receive an extra roll every time they knock down all ten pins; up to a maximum of three total rolls.

## The Challenge

In this challenge you will be given a string representing a player's ten frames. It will look something like this: 'X X 9/ 80 X X 90 8/ 7/ 44' (in Java: "X X 9/ 80 X X 90 8/ 7/ 44"), where each frame is space-delimited, 'X' represents strikes, and '/' represents spares. Your goal is take in this string of frames into a function called bowlingScore and return the players total score.

## Scoring

The scoring for ten-pin bowling can be difficult to understand, and if you're like most people, easily forgotten if you don't play often. Here is a quick breakdown:

## Frames

In Ten-Pin Bowling there are ten frames per game. Frames are the players turn to bowl, which can be multiple rolls. The first 9 frames you get 2 rolls maximum to try to get all 10 pins down. On the 10th or last frame a player will receive an extra roll each time they get all ten pins down to a maximum of three total rolls. Also on the last frame bonuses are not awarded for strikes and spares moving forward.

In this challenge, three frames might be represented like this: 54 72 44. In this case, the player has had three frames. On their first frame they scored 9 points (5 + 4), on their second frame they scored 9 points (7 + 2) and on their third frame they scored 8 points (4 + 4). This is a very simple example of bowling scoring. It gets more complicated when we introduce strikes and spares.

## Strikes

Represented in this challenge as 'X'

A strike is scored when a player knocks all ten pins down in one roll. In the first 9 frames this will conclude the players turn and it will be scored as 10 points plus the points received from the next two rolls. So if a player were to have two frames X 54, the total score of those two frames would be 28. The first frame would be worth 19 (10 + 5 + 4) and the second frame would be worth 9 (5 + 4).

A perfect game in bowling is 12 strikes in a row and would be represented like this 'X X X X X X X X X XXX' (in Java: "X X X X X X X X X XXX"). This adds up to a total score of 300.

## Spares

Represented in this challenge as '/'

A spare is scored when a player knocks down all ten pins in two rolls. In the first 9 frames this will be scored as 10 points plus the next roll. So if a player were to have two frames 9/ 54, the total score of the two frames would be 24. The first frame would be worth 15 (10 + 5) and the second frame would be worth 9 (5 + 4).

For a more detailed explanation see Wikipedia:

http://en.wikipedia.org/wiki/Ten-pin_bowling#Scoring

## How I solved it

I used basic ladder logic to solve it (and a fair amount of using Chrome's debugging tools!) Here is my solution:

        // Let's initiate our function!
    function bowlingScore(frames) {
    
      // Split apart the string of frame scores
      var scoreArr = frames.split(" ");
        
        // Set up the array to handle the multidimensional array
      var concArr = [];
        
        // Initiate our total score
      var total = 0;
      
        // Fill concArr with all of the frame items
      for (var i = 0; i < scoreArr.length; i++) {
         concArr.push(scoreArr[i].split(''));
      }  
        
        // Add an extra array to concArr so that we don't have issues later.
       concArr.push(0, 0);
    
    	// Loop through frames
      for (var z = 0; z < 10; z++) {
	      
	      // Loop through frame items 0 and 1
        for (var x = 0; x < 2; x++) {
    
    		// Strike!
    		if (concArr[z][x] == "X") {
	    		
    			// What are the future frames?
    
    				// Do the second and third frame items have strikes? XXX
	    		if (concArr[z][1] == "X" && concArr[z][2] == "X" && x == 0) {  
	    			total += 30;
	    	
            // Does the second frame item have a strike and the third an integer?
          } else if (concArr[z][1] == "X" && isInt(concArr[z][2]) && x == 0) {  
          				total += 20 + parseInt(concArr[z][2]); 
                
    				// Does the second frame item have a strike? XX
     			} else if (concArr[z][1] == "X" && x == 0) {  
    				total += 20;
		  
    				// If the above fails, then we have a strike or spare and need to look at the next frames.
				
    				// The next frame is a strike!
    			} else if (concArr[z+1][0] == "X" && x == 0) {
    		
    						// What is the third frame out?
    
    						// If the third frame out is a strike too
    					if (concArr[z+2][0] == "X") {
    						total += 30;
                        
                // Third frame out is a spare
              } else if (x == 0 && concArr[z+2][1] == "/") {
                 total += 20 + parseInt(concArr[z+2][x])
                            
                // If this is the 9th frame & at least two strikes in the last frame
              } else if (concArr[z+1][1] == "X" || concArr[z+1][1] == "/" ){
                  total += 30;
                        
                // If the third frame out is not a strike
	    				} else if (isInt(concArr[z+2][x]) && x == 0){
	    					total += 20 + parseInt(concArr[z+2][x]);
    					}

              // The next frame is a spare!
    			} else if (concArr[z+1][1] === "/" && x == 0) {
    				total += 20;
                
              // Was the next frame just a couple of integers?
    			} else if (x == 0)  {
    				total += 10 + parseInt(concArr[z+1][0]) + parseInt(concArr[z+1][1]);
    			}

    			// Spare!
    		} else if (concArr[z][1] == "/") {
                
              // Next frame has a strike or this is the tenth frame with a strike at the end
    				if (x == 0 && (concArr[z+1][0] == "X" || concArr[z][2] == "X")) {
	    				total += 20
                    
              // This is the tenth frame with a number of pins down at the end
             } else if (x == 0 && parseInt(concArr[z][2])) {
               total += 10 + parseInt(concArr[z][2]);
                    
           // Next frame is just a regular integer
				} else if (x == 0) {
					total += 10 + parseInt(concArr[z+1][0]);
				}
		
    		// Maybe you hit something?
          } else if (isInt(concArr[z][x])){
            total += parseInt(concArr[z][x]);
          } 
        }
      }
  
    return total;
    }
    
        // Making a function for an additional toolset.
        // Gotta make sure that we don't accidentally take some NaNs or undefined variables with us!
    function isInt(value) {
        
        // We get ready to handle an item
      var x;
        
        // First check if it is NaN
      if (isNaN(value)) {
        return false;
      }
        
        // Now, we see if it is a number at all
      x = parseFloat(value);
        
        // Since we know that it's a number, let's check if it is an integer & return the result.
      return (x | 0) === x;
    }

