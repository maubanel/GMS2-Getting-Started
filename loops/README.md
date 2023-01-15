<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### GMS2 Loops

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

This tutorial is intended for those wanting an introduction to <i>GameMaker Studio 2</i> using their scrpting language <i>GML</i>. This assumes no prior knowledge of the software or scripting. This walk through looks at [loops](https://manual.yoyogames.com/GameMaker_Language/GML_Overview/Language_Features/for.htm) in GMS2. This is a fundamental feature of most programming languages and it allows us to run an statement multiple times.

A loop repeats itself a given number of times within one frame to perform a set of operations.  In a game we might be looping through all enemies to see which is closest to the player to auto aim a reticule.

* Tested on GameMake Studio2.3.5.589
* An existing [GML Project](https://github.com/maubanel/GMS2-Snippets/blob/main/rename-project/README.md#user-content-rename-gms2-project)

<br>

---

##### `Step 1.`\|`ITB`|:small_blue_diamond:

Create a new room by *left clicking* on **Rooms** arrow in the **Asset Browser** to open up the rooms list.  *Right click* and select **Rename** and call it `rm_loop`. Go to **Room Order** and move it to the top of the list if you have other rooms in this project.

![rename Room1 to rm_loop and move it to the top of the list](images/loopRoom.gif)


<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Right click on **Objects** in the **Asset Browser** and select **Create | Object**.  Call this object `obj_loop`.  Press the **Events | Add Events | Draw | Draw** to add a draw event. 

![create new object called obj_loop and add draw event](images/addLoopObj.gif)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now drag an instance of **obj_loop** into the room **rm_loop**

![add obj_loop to room](images/addObjLoopToRoom.png)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITB`| :small_orange_diamond:

We will look at two loops supported in GameMaker.  The first is **[repeat](https://manual.yoyogames.com/GameMaker_Language/GML_Overview/Language_Features/repeat.htm)**.

So lets look at programming a loop to see what it does. Lets create a list of what we want to do in this next portion of our script:

* Center align text
* Add a title
* Add a variable called loop_num
* Print value of loop_num under title
* Add a `repeat(5)` loop which runs what is inside the following curly braces five times
* Add 1 each time the loop runs to the loop_num variable
* Print value of loop_num after it runs through the loop
* Reset text alignmnet

![Add a loop that repeats 5 times and adds one to a variable](images/repeatLoop.png)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

Now *press* the <kbd>Play</kbd> button in the top menu bar to launch the game. Notice that all the items in our list are addressed. Most importantly we can see that loop_num goes from 0 to 5 proving that the loop ran 5 times.

![Repeat statement running in game](images/repeatLoopInGame.png)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Sometimes we need to access a value of where in the loop we are at.  Other times we sometimes don't know how many times we need to loop (go through each enemy still alive in level). There is another type of loop that you can use called a **[for loop](https://manual.yoyogames.com/GameMaker_Language/GML_Overview/Language_Features/for.htm)**.  A for loop looks a bit more complicated:

* Starts with an initial value (often starts at 0 but doesn't have to)
* Condition that when it is still true will keep looping (exit condition)
* Do this after a pass through the loop 

These three items are separated by a ; (semi-colon). 


!["Add a loop that repeats 5 times and adds one to a variable](images/forLoopScript.png)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

These above creates a new **variable** called `i`.  It exits the loop when `i` gets to `6` or above.  After each time through the loop `i` is incremented by `1`. We use the index value `i` to add spacing to the text as we will be adding 5 lines.

Now *press* the <kbd>Play</kbd> button in the top menu bar to launch the game. We should see 5 lines printing the value of the index i.

![For loop running in game](images/forLoopInGame.png)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **File | Save Project** then press **File | Quit** to make sure everything in the game is saved. If you are using **GitHub** open up **GitHub Desktop** and add a title and longer description (if necessary) and press the <kbd>Commit to main</kbd> button. Finish by pressing **Push origin** to update the server with the latest changes.

![save, quit, commit and push to github](images/GitHub.png)

| `gms2.loops`\|`THE END`| 
| :--- |
| **That's All Folks!** no more looping. |

___

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=The End!">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

