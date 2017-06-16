Today's task is: "to make a function that can take any non-negative integer as a argument and return it with it's digits in descending order. Essentially, rearrange the digits to create the highest possible number."

The examples are:

Input: 21445 Output: 54421
Input: 145263 Output: 654321
Input: 1254859723 Output: 9875543221

This one was relatively simple. For that reason, I decided to see how much I could do with one jQuery expression. Here is my solution:

      // This function will take an integer and sort it into descending order.
    function descendingOrder(n){
    
      /* 
      This performs several steps:
      1) Convert the entire thing to an integer with base 10 to satisfy the requirements
      2) Convert the variable "n" to a string so that we can manipulate it
      3) Split the string up into an array
      4) Sort the array into descending order
      5) Concantenate the array into a string which will be handled in step 1
      6) Done!
      */
      return parseInt(n.toString().split('').sort(function(a, b){return b-a}).join(''), 10);
      
    }
