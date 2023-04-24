Editor
======

The Chattr editor is quite simple.
It contains 3 sections:

* The file browser
* The player setup
* The text editor

File Browser
------------

The biggest part of the file browser is the file tree.
By default it shows all ``.chattr`` files and the folders that contain them.
Clicking a script will open it in the text editor.
Opening a new script will autosave anything that was previously open.
The editor also autosaves your work periodically.

Above is a text field labeled "filter". This allows you to filter
the file tree to quickly find what you want. Next to the text box
is a refresh button that rescans the filesystem and updates the 
tree accordingly.

At the top of the file browser is a switch labeled "Show All Folders".
When on, this will make the file tree display all folders in the game
directory, regardless of if they contain Chattr files. This is useful 
for adding the first Chattr script to a directory, since normally 
directories don't show until there is already at least one script inside.

At the bottom is a row of three buttons. The leftmost one adds a file/folder
in the current directory. The middle one renames the currently selected file/folder.
The rightmost one deletes the currently selected file/folder.

Player Setup
------------

Below the file browser is a text box.
In here, enter the names of the players you wish to be
present while testing your scripts, each on a separate line.

Text Editor
-----------

The right side of the editor is where you edit your scripts.
The editor is complete with error reporting (partially),
syntax highlighting, and code completion (TBA).

Above the text editor is a toolbar displaying the currently open path,
the caret's line and column, and two buttons for testing.
The left button compiles your script, displaying a checkmark when successful
and an 'x' when unsuccessful. The right button compiles `and` runs the script
in the testing environment.

Below the text editor is where you'll see the details of error reports.