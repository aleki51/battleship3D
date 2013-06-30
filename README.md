*********************************************
*  PROJECT : Battleship Game				        *
*	VERSION : 1.0							                *
*	AUTHOR  : Alexis BERARD					          *
*	CONTACT : alexis.berard@gmail.com		      *
*	Copyright © 2013. All Rights Reserved     * 
*********************************************

PROJECT DESCRIPTION
*******************

This program is the first version of a battleship game. It is  Player vs Player version, no AI for the moment. 
This game follows the rules described in the official documentation downloadable from Hasbro’s website (a copy is available in the main folder).  
The development has been done using OpenGL for the 3D rendering and the QT framework (based on Qt4.5) for the c++ classes and the user interface.
This program also displays 3d ships based on models designed with 3DS MAX and found on internet. The code that enables to load and displays these models 
is a modified version of the work published by  Mark M. Lanning. http://www.planet-source-code.com/vb/scripts/ShowCode.asp?txtCodeId=6125&lngWId=3.
More generally, the global design of this program is based on the Model View Controler architecture. 
A few screenshots are available in the main folder for your own review.    

INSTALL
*******

You just need to unzip the archive and extract the main folder wherever you want on your computer. 

CONFIGURATION
*************

For a proper execution, you have to make sure that the following points are respected : 
- the images, config file and 3ds files must remain in the folders respectively called “img”, “config” and “3dmodels”
- the dll files (for windows users)  must stay in the same folder where the exe file is located.

If you wish to recompile the code, you must use Qt4.7 or older as the latest releases (Qt4.8 and even Qt5 handle opengl in a different way). 
A new version of this program working this time with qt4.8 at least will be released soon. Anyway, the compiling step should be straight forward, 
no matters what operating system you are using as Qt is supported by any of them. 

FEATURES
********

- This game allows 2 users to play on a 3d plateform (10x10 grid). For a more efficient rendering, display lists are used to store grid vertices, 3d meshs vertices and textures.

- Both user can create their own fleet using the config file. The user must respect the XML syntax and can only use 5 types of ships : carrier, battleship, destroyer, submarine, cruiser. 
A set of tests will be performed at the beginning of the program to check if each ship’s data is correct (existing type, positions, XML syntax, etc). The big advantage of using such a declaration file 
is that it allows the users to try any sort of fleet. For example, Player 1 can use 4 destroyers and one submarine whereas Player 2 will play with 2 cruisers and 1 carrier. 
Any kind of fleet is possible as long as the XML data are correct. 
- The user can select his target by using the mouse and clicking on the appropriate cell on the top half of the game board. He also can use to keyboard to move the camera backward or forward to look at a ship hidden 
behind another one for example. Left and right rotations are also possible to have a look at the background which is the result of the cube mapping technique.
- The user can also change the colors of the grid and the board using the setting button. That way, he can also select another type of background. 
- Each time a missil is launched, a popup dialog box appears and informs the current user with the appropriate message, if he hit a ship or not and even if he won the battle. 

BUGS
****

- The program does not quit in a proper way when the user clicks on the X button at the top right corner.
- A tiny white line appears at the border of some side of the textured cube.    

FUTURE WORK
***********

- Create a .ini file where all the static variables values(widget size, file names etc) will be stored instead of beeing forced to modify (and recompile) the code.
- Allow the user to launch not only one missil but a salvo (as many missils as the remaining ships)
- An Artifical Intelligence is planned to be developed so a user can play against the computer.Firstly that AI would have a simple algorithm as described below : 
		*Fire randomly until a ship is hit. 
		*if a ship is hit
			*stack up the the four surrounding grid squares as 'potential' targets (or less than four if the cell was on an edge/corner). Cells are only added if they have not already been visited.
			*Then while the ship is not sunk or the stack empty. pop the next potential target off the stack and fires at this location. Update the stack if it’s a hit or pop off the next element on the stack
		*Restart firing randomly until another ship is hit
- A better exceptions handler has to be developed, not to only handle wrong xml data at this is the case at the moment, but also to catch exceptions from data structures or even the graphic card.
- A feature enabling the user to load and save games will be also added.  
- 3D objects will be rendered using Vertex Buffer Objects instead of display list. A FPS counter will be also implemented to measure the efficiency of such a method. 
- A graphic module will be added at the beginning of the program so the user can drag and drop his ships on a map when creating his fleet instead of declaring everything in an XML file
- The graphical rendering has to be more immersive. The popup dialog box will be replaced by sounds and explosion or particules effects
- Ultimately, the integration of qt3d or an external graphic engine will be ideal.  
