# Orientation Course - Basics of JavaScript Programming

MP 9/2020

## JavaScript assignment 2

Make an application that simulates a [Rock paper scissors](https://en.wikipedia.org/wiki/Rock_paper_scissors) game.

- Start with [this tutorial](https://www.youtube.com/watch?v=qWPtKtYEsN4)
- Download the png image files from Oma
- This time it's ok to modify html and css freely to style your game

- Video tutorial at 30:15: use a for-of loop instead of `array.forEach()` (the modern way)
  - you can use the arrow function syntax for event handler functions, just use the name of the variable instead of `this`, example:

  ```js
  for (const option of options) {
    option.addEventListener("click", () => {
      // option refers to current item, no need for 'this'
      console.log(option);
    });
  }
  ```

  - same syntax works with `animationend` events too

NOTE: this is and individual task

### Functional requirements

- all the functionalities implemented in the tutorial
- game ends after 10 wins for a player or computer (similar idea is described in the end of the video tutorial)
  - show a message telling who won the whole game
- game ends also if a player wins 3 times in a row
  - an idea: use an array to record wins/results asnd check after every round if the three latest items match

### Returning

- Check instructions in Oma assignments
- upload the application to your _public_html/_ and return working a web link to Oma
- return all files to Oma in a ZIP file

### Grading

0-5 points.

- working application based on the tutorial with some custom styling: 2 points
- all functional requirements implemented: +3 points
- EXTRA: design and implement an extra feature to you app + 0-1 point
  - explain the idea of the feature when returning assignment to Oma
- Messy code, hard to read and understand, comments mssing, etc.: minus points
- Returned after deadline to Oma: 1-5 minus points (more than a week late -> don't bother anymore)
