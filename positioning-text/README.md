![](../images/line3.png)

### GMS2 Positioning Text

<sub>[previous](../setting-up/README.md#user-content-setting-up) • [home](../README.md#user-content-gamemaker-studio-2-getting-started) • [next](../data-types/README.md#user-content-gms2-data-types)</sub>

![](../images/line3.png)

This tutorial is intended for those wanting an introduction to <i>GameMaker Studio 2</i> using their scrpting language <i>GML</i>. This assumes no prior knowledge of the software or scripting. This walk through looks at how to add text to a 2-D game level and position it in the dead center on screen.

* Tested on GameMake Studio2.3.5.589
* An existing [GML Project](https://github.com/maubanel/GMS2-Snippets/blob/main/rename-project/README.md#user-content-rename-gms2-project)

<br>

---

##### `Step 1.`\|`ITA`|:small_blue_diamond:

In GameMaker all of our resources are stored in the **Resources** menu.  By default it is in the right hand side of the screen (although you can change its location as these tabs can be redocked).  Each of these sections have a small triangle that can be expanded or minimized to show the assets of that class.  All of our art, audio, scripting and other elements will be stored here in the appropriate folder.  


All projects in **GameMaker Studio 2** start with a room called **room0**. A room represents a level of your game.  You can have multiple rooms thus multiple levels. If you don't see the room in the **Resources** menu then *press the right arrow* next to the **Rooms** title to open up all the rooms in this folder. Double left click **room0** to open it.  If you don't see the room in the editor, you can then *press the middle Zoom icon* with the **=** in it to reset the zoom level.

![alt_text](images/OpenDefaultRoom.gif)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Now we should rename the room to something more appropriate.  It is a good idea to always preface the names with what Resource type we are using.  We will prepend the room names with `rm_` and call it `rm_hello_world` by *right clicking* on the room and selecting **Rename**</b> from the drop down menu and then type in the new name for the room.

![rename room to rm_hello_world](images/RenameRoom.gif)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go to the **Resources** menu on the right and *right click* on the **Object** heading that is partially greyed out.  *Select* **Create Object**, this will add the default **Game Object** to our **Workspace**.  Notice that in our main window it has a tab that says **Workspace1**  This is the area where we will be customizing the game object.  Go to the **Name** input box and change the **Name** from **object1** to `obj_hello_world_text`.

![create a new object called obj_hello_world_text](images/CreateHWObject.gif)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we have a game object.  Normally we would attach an animation to it to play in the game.  In this case we will use the object to draw text on the screen.  GameMaker objects are controlled through [Object Events](https://manual.yoyogames.com/The_Asset_Editors/Object_Properties/Object_Events.htm)

> "These events fall into two categories: those that run every single game step, and those that are "triggered" by a game event, like the instance reaching the room edge or a keyboard or mouse press. - GameMaker Manual"

In this case we do not have any art to attach to the sprite so we will need to draw a font on screen through a script.  This is done through a **Draw** object event.  All the draw events are a type that run **every** step.  There are different types of draw events but the two we will care about now are **Draw** and **Draw GUI**.  **Draw GUI** will draw to the screen space and will be in the same portion of the camera regardless of where the camera is located in the level.  With a regular **Draw** event the draw will be relative to the room and will not move with the camera.  Since we want to place this text in the level we will use a draw event. *Double click* `obj_hello_world_text` to center it in our workspace. *Left click* on the **Add Event** button in the **Events** tab of the game object and select **Draw | Draw**. This will bring out a scripting window that will allow us to add some game logic to this event type.

![add draw event to game object](images/AddDrawEvent.gif)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITA`| :small_orange_diamond:

This brings up a scripting tab (notice the green lines connect the related tabs together so you don't get confused).  This is where we add scripting for game logic.  The very first thing we are going to start with is add comments.  When you are starting out this is usually the part that is counter-intuitive.  When we write an essay we usually don't add comments to describe what we are writing.  
		
With game logic it is important to document what we are doing as if we come back to it in a few weeks, we will have forgot what we have done.  It is better to err on too many and verbose a comment than none at all.  It will not affect the performance of the game and the player will never end up seeing them (they will not get compiled into the playable build). Comments are not interpreted by the computer and don't turn into logic.  They are human readable and are for the development team.  

If you have two forward slashes `//` everything that follows on that line is a comment and in GameMaker's default settings turns green. This is for human reading and does not affect the game at all.  You can add as much as you will like.
		
I added:

```
/// @Draws Hello World On Screen
// Draw Hello World
```

![add code comments](images/CommentsOnDrawEvent.png)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

To draw text to a screen we need to call a [Function](https://manual.yoyogames.com/#t=GameMaker_Language%2FGML_Overview%2FRuntime_Functions.htm&rhsearch=function&rhhlterm=function).  What is a function?  It is a way of allowing us to do a similar task over and over again without retyping all the code again.  If you are copying and pasting the same blocks of code to use in multiple places, you should consider turning it into a function.  

Think of the function as a factory.  That factory can receive input and it can output one thing for you.  For example we might have a function called `average(num, num, num ...)`.  This calls a function named **average** and will send it multiple numbers (the numbers passed in parenthesis).  Lets look at this in Pseudo Code:

```
average(3, 8, 10);
```

A function is a name followed by a set of parentheses.  Inside the parenthesis are **Parameters** that are passed to the function.  These are comma separated (spaces don't matter here).  In this case we are passing three number parameters to this function. This function would return the average of these three numbers (the equivalend of (3 + 8 + 10) / 3) which is 7.

In our case we will be calling a function named **[draw_text](https://manual.yoyogames.com/#t=GameMaker_Language%2FGML_Reference%2FDrawing%2FText%2Fdraw_text.htm&rhsearch=draw_text&rhhlterm=draw_text)**. This takes three arguments.  It takes an **x** position in the room, a **y** position in the room and a **string** (a group of letters, numbers and symbols). Lets now call this function.  For the **x** and **y** argument we will not pass it numbers.  Please note that if you look at the help menu that this function does not return any value (the manual says it returns **NA** - not applicable).
		
We will use the **x** and **y**  position of the object in the room.  There are two built in variables in each game object and this is its x,y position in room space.  So type in **obj_hello_world_text: Draw** event:

![add draw_text code to game](images/DrawHelloWorldHardCoded.png)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

The above should draw the text "Hello World" (without quotation marks) in the room.  But first we need to drag this game object in the room so it knows to run this game object in this level we previously named. So we *double left click* on the **rm_hello_world** to go back (or reopen) the room.  *Adjust* the zoom so you can see the entire room as we want to *drag* the game object in the center.  Make sure the **Layers** tab in open in the **Room Editor** and that you highlight **Instances** layer.  You can only add game objects onto an instance layer (you can have more than one layer of course).  Then drag and drop a single instance of **obj_hello_world_text** into the main game window in as close to the center as you can make it:

![add obj_hello_world_text to room](images/PlaceHelloWorldObjectInRoom.png)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

I eyeballed the center of the room.  What if I want it to be in the exact center of the room.  How do I go about doing this?  I can *double left click* on the **icon** in the middle of the room which will bring up an **Instance** window of this game object.  I can look at the **Properties | Room Settings | Width & Height** to see the pixel dimensions of the room.  In my case it defaults to `1366` by `768`.  The center would be these two values divided by 2.  So if your instance window does not show **x** as `683` and **y** as `384`, make the change to them in the editor window now so that the object is dead center.

![center object in room](images/CenterOfRoom.png)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we are ready to run the game for the first time.  I know this is not impressive but this is the least we need to have something in a game.  We need a room and a game object with some logic.  Press the <kbd>Play</kbd> button in the top menu bar to launch the game.  It should look like this:

![Game Running Hello World](images/HelloWorldGame.png)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITA`| :large_blue_diamond:

Notice that the text is left justified.  It starts writing from the center going towards the right hand side.

![Showing center of room in running hello world](images/HelloWorldGameOffCenter.png)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

What if we wanted to center the text on the screen?  We can call another function to adjust how the text is aligned horizontally.  It is conveniently called **[draw_set_halign(halign)](https://manual.yoyogames.com/#t=GameMaker_Language%2FGML_Reference%2FDrawing%2FText%2Fdraw_get_halign.htm&rhsearch=draw_set_align&rhhlterm=draw_set_align)**. This function again does not return anything, it just sets the horizontal alignment.  What is the argument `halign`?  This is not a number and is not a string.  It is an **[enumerator](https://manual.yoyogames.com/#t=GameMaker_Language%2FGML_Overview%2FData_Types.htm&rhsearch=enumerator&rhhlterm=enumerator)** (will get into detail in another tutorial) that lists the types of alignment in english.  The enumerator we want is called `fa_center`.  Go back to the script window in **obj_hello_world_text: Draw** and on the very top (above the `draw_text(string)` function just start to type `draw_set_halign`.

![Type draw_set_halign in draw event auto-complete](images/AutoCompleteDrawSetHalign.png)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

You will notice that the engine starts to give you possible suggestions in the auto-complete.  If you type enough it will narrow it down to its one built in function.  You don't need to continue typing.  If it is highlighted you can just press the <kbd>Enter</kbd> or <kbd>Tab</kbd> to fill in the rest for you. The advantage is not only speed but it prevents spelling errors which causes the game to not compile or run.

Now in the parenthesis start to type the parameter `fa_center` and then auto-complete.

![selecting fa_center enum to pass to draw_set_halign](images/FaCenterTextHAlign.png)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Add a comment to explain what this does on top of the function (your comment does not have to be the same as mine, as long as it makes sense to you and/or your team).  It should look like:


![Add another comment to what you just typed](images/CenterHalign.png)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

This does not affect the alignment for this one object.  The draw event is global and it will change the alignmnet for all other objects in this level. Now at the end lets return back to the default.  Otherwise it is possible that this will affect the horizontal alignment of other future objects.  So set the horizontal alignment back to `fa_left`.

![reset alignment at end to left](images/ReturnToFALeft.png)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

*Run* the game again by pressing the <kbe>Play Button</kbd> in the top menu bar to launch the game.  Now the text should be horizontally centered. It should look like this:

![Game runs hellow world with proper centering](images/HelloWorldInGameCenter.png)

<img src="![](../images/line2.png)" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond:

Select the **File | Save Project** then press **File | Quit** to make sure everything in the game is saved. If you are using **GitHub** open up **GitHub Desktop** and add a title and longer description (if necessary) and press the <kbd>Commit to main</kbd> button. Finish by pressing **Push origin** to update the server with the latest changes.

![save, quit, commit and push to github](images/GitHub.png)

| `gms2.positioning-text`\|`THE END`| 
| :--- |
| **That's All Folks!** That's it for this snippet. |

___


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up Data Types"> -->
![Next Up Data Types](images/banner.png)

![](../images/line.png)

| [previous](../setting-up/README.md#user-content-setting-up)| [home](../README.md#user-content-gamemaker-studio-2-getting-started) | [next](../data-types/README.md#user-content-gms2-data-types)|
|---|---|---|

