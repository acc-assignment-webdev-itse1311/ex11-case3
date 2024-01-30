# NP HTML5, CSS3, and JavaScript 6e Tutorial 11, Case Problem 3

## Description:
1.  Use your editor to open the pc_cword_txt.html and pc_cword_txt.js files from the html11 > case3 folder. Enter your name and the date in the comment section of each file, and save them as pc_cword.html and pc_cword.js respectively.
2.  Go to the pc_cword.html file in your editor. Link the file to the pc_cword.css file containing the styles for the crossword puzzle table and clues list. Asynchronously load the script from pc_cword.js file.
3.  Take some time to study the contents of the table. Note the values of the different data-* attri¬butes used to identify the different span elements of the crossword puzzle and note the IDs of the puzzle letters and the puzzle clues. Save your changes to the file.
4.  Return to the pc_cword.js file in your editor. Below the initial comment section, declare the fol¬lowing global variables:
    a.  allLetters, which will be used to reference all letters in the crossword puzzle
    b.  currentLetter, which will be used to reference the letter currently selected in the puzzle
    c.  wordLetters, which will be used to reference the letters used in the currently selected across and down clues
    d.  acrossdue, which will be used to reference the across clue currently selected in the puzzle
    e.  downclue, which will be used to reference the down clue currently selected in the puzzle
    f.  typeDirection, which stores the current typing direction (either to the right or down); set its initial value to "right"
5.  Add a command to run the init() function when the page loads.
6.  Create the init() function, which sets up the initial conditions of the puzzle. Add the following commands to the function:
    a.  Set allLetters to reference the elements using the selector table#crossword span.
    b.  Set currentLetter to reference the first object in allLetters collection
    c.  Explore Declare the acrossID variable, setting its value equal to the value of the data-clue-a attribute for currentLetter. Declare the downiD variable, setting its value equal to the value of the data-clue-d attribute for currentLetter.
    d.  Set the value of acrossClue to reference the element with the id attribute "acrossID". Set the value of downClue to reference the element with the id attribute "downID".
7. Next, create the formatPuzzle() function. This function will format the colors of the crossword table cells and the clues in the clues list based on the letter that is selected by user. The function has a single parameter named puzzleLetter. Add the following commands to the function:
   a.  Change the value of currentLetter to puzzleLetter.
   b.  Remove the current colors in the puzzle by looping through all items in the allLetters object collection, changing the background-color style of each to an empty text string.
   c.  After the for loop, remove the highlighting of the current clues by changing the color style of acrossClue and downClue to an empty text string.
   d.  Explore Determine whether there exists an across clue for the current letter by testing whether currentLetter.dataset.clueA is not equal to undefined. If true, then do the following:
   i.  Set acrossClue to reference the element with the ID value of currentLetter.dataset. clueA in order to reference the across clue for the current letter.
   ii.  Change the color style of acrossClue to blue.
   iii.  Set wordLetters to reference all elements selected by the CSS selector [data-clue-A = clue] where clue is the value of data-clue-a for currentLetter.
   iv.  Change the background-color style of every item in wordLetters to the light blue color value rgb(231, 231, 255).
   e.  Repeat Step d for the down clue indicated by the data-clue-d attribute, changing the color style of downClue to red and the background-color style of the items in wordLetters to the light red color value rgb(255, 231, 231).
   f.  Indicate the typing direction for the current letter. If typeDirection = "right", change the background color of currentLetter to the blue color value rgb(191, 191, 255); otherwise, change the background color to the red color value rgb(255, 191, 191).
8. Return to the init() function and add the following commands to apply the formatPuzzle() function:
   a.  Color the crossword puzzle's first letter by calling the formatPuzzle() function using currentLetter as the parameter value.
   b.  Users should be able to select a puzzle cell using their mouse. Loop through the items in the allLetters object collection and for each item:
   i.  Change the cursor style to pointer.
   ii.  Add onmousedown event handler that runs an anonymous function calling the formatPuzzle() function using the event object target as the parameter value.
9. Create the selectLetter() function. The purpose of this function is to allow users to select puzzle cells using the keyboard. Add the following commands to the function:
   a.  Declare the leftLetter, upLetter, rightLetter, and downLetter variables and set their values to reference the letters to the left, above, to the right, and below the current letter selected in the table. (Hint: use the dataset.left, dataset.up, dataset.right, and dataset.down properties of currentLetter.)
   b.  Explore  Store the code of the key pressed by the user in the userKey variable. (Hint: use the keyCode property of the event object to retrieve the key code value.)
   c.  Add the following if-else structure to determine the program response based on the value of userKey:
   i.  If userKey equals 37 (the left arrow key), call the formatPuzzle() function using leftLetter as the parameter value
   ii.  If userKey equals 38 (the up arrow key), call formatPuzzle() with the upLetter variable.
   iii.  If userKey equals 39 or 9 (the right arrow and tab keys), call formatPuzzle() with the rightLetter variable.
   iv.  If userKey equals 40 or 13 (the down arrow and enter keys), call formatPuzzle() with the downLetter variable.
   v.  If the userKey equals 8 or 46 (the backspace or delete keys), delete the text content of currentLetter.
   vi.  If userKey equals 32 (the spacebar key), run the switchTypeDirection() function to change the typing direction.
   vii.  If the code value is between 65 and 90 (the letters a through z), write the character into the cell by changing the text content of currentLetter to the value returned by the getChar() function using userKey as the parameter value and then move to the next cell in the puzzle. If typeDirection is "right", move to the next cell by calling the formatPuzzle() function with the rightLetter variable; otherwise, go down to the next cell by calling the format- Puzzle() variable with the downLetter variable.
   d.  After the if-else structure, enter a command to prevent the browser from performing the default action in response to the keyboard event.
10.  Return to the init() function and add an event handler to run the selectLetter() function in response to the keydown event occurring within the document.
11.  Create the switchTypeDirection() function to toggle the typing direction between right and down. Add the following commands to the function:
     a.  Declare the variable typelmage that points to the element with the ID "directionImg".
     b.  Create an if-else structure that tests the value of the typeDirection global variable.
     c.  If typeDirection = "right", then change typeDirection to "down", change the src attribute of typeImage to "pc_right.png", and change the background color of currentLetter to the red color value rgb(255, 191, 191); otherwise change the typeDirection to "right", change the src attribute of typeImage to "pc_down.png", and change the background color of current letter to rgb(191, 191, 255).
12.  Users can change the typing direction either by using the keyboard or by clicking the pointer on an image located below the crossword puzzle. Return to the init() function and add the following commands:
     a.  Declare the variable typeimage referencing the element with the ID "directionImg".
     b.  Change the cursor style of type Image to "pointer".
     c.  Run the switchTypeDirection() function when the typeImage is clicked
13.  Bernard wants users to be able to briefly view their mistakes. Add an onclick event handler to the init() function that runs the following commands when the user clicks the Show Errors button:
     a.  Loop through all items in the allLetters object collection. If the text content of an item does not match the value of the letter's dataset.letter property, change the color style of the letter to red.
     b.  After a 3-second interval, set the color style for the items in the allLetters collection to an empty text string, restoring the letters to the default font color.
14.  Complete the init() function by adding an onclick event handler to the Show Solution button. In response to the click event, run an anonymous function containing a for loop that goes through all items in the allLetters collection, setting the text content of each item to the value of the letter's dataset.letter property.
15.  Document your solution by commenting your code and then save your file.
16.  Open the pc_cword.html file in your browser. Verify your solution by doing the following:
     a.  Navigate through the puzzle using the arrow keys, Tab key, and Enter key
     b.  Select a puzzle cell using the mouse
     c.  Confirm that the across cells and across numbered clue for the selected cell are highlighted in
     blue and the down cells and down numbered clue are highlighted in red
     d.  Press the spacebar or click the direction image to verify that the typing direction and image
     toggles between right and down and that the color of the active cell indicates the typing
     direction
     e.  Delete the current letter by either pressing the Delete key or the Backspace key
     f.  Briefly highlight puzzle mistakes by clicking the Show Errors button
     g.  View the complete solution by clicking the Show Solution button
