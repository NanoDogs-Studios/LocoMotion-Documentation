# LocoConsole (LocoMotion: The Revival)

The LocoConsole or LocoMotion: The Revival Console is a console that makes it easy for players and users to access specific features about LocoMotion. Similar to [Valve Source Engine's Console](https://developer.valvesoftware.com/wiki/Developer_console), It also makes it easy for modders to make their own commands and others. this is the documentation 
Below is a list to all console commands.

## Log

Format example: log "this is the format! you can have as much text in this string as you want!"
Command Name: log
Description: Print a message to the console.
Additional Notes: none

## Map

Format example: map "Level 1"
Command Name: map
Description: Changes scene to a specific one. (ensure correct scene name, refer to documentation for details.)
Alternate Commands: changemap
Additional Notes: make sure the scene name matches the inputed string, example: map "Level 1"
Map List (In order of build index):

0. Boot
1. Menu
2. OutdoorsScene
3. Level 1
4. Level 2
5. LocoEditor
6. Multiplayer.unity #5 2

If you do not know how to use unity's SceneManagement.LoadScene() function, here is a breif explanation:
Unity sees it scenes as maps in your build settings, the first being a build index as 0. you can also use this as a map name in the map command. example: map "0", to load into boot.


## God

Format example: god
Command Name: god
Description: Toggles god mode.
Additional Notes: None

## Kill
Format example: kill
Command Name: kill
Description: Kills you.
Alternate Commands: suicide
Additional Notes: None

## Killplayer

Format example: killplayer "LaymPuppeh"
Command Name: killplayer
Description: Kills a player in the lobby (host-only).
Additional Notes: Can only be activated in Multiplayer and you must be the host of the lobby.

## Debug

Format example: debug
Command Name: debug
Description: Enables the debug menu, allowing adjustment for all movement variables, including speed and jump force.
Addition Notes: Please note: if some features are missing from the debug menu, it is still in development.


## Showtriggers

Format example: showtriggers
Command Name: showtriggers
Description: Shows all the box colliders with isTrigger on
Additional Notes: Can also be activated with Debug Menu (debug).

## IN DEVELOPMENT:
Keep in mind, these commands are still being changed and more commands are being created.

# Guide: Create a LocoCommand
with the LocoModding tools and libary, create a new c# project, and create a new class to initalize LocoModding. then create another class, called your command (note: it must be 1 word.) once in your class,
derive from the `` : LocoCommand ``.  and wrap it with the``Loco.Commands`` Namespace. then create A public with your command name and in that add a variable for ``CommandName`` and ``Description`` both of which are a string, once again make sure you ``CommandName`` Variable is a single word or joined, example of everything so far:

```
using UnityEngine;

namespace Loco.Commands
{
    public class MyCommand : LocoCommand
    {
        public MyCommand()
        {
            CommandName = "mycommand";
            Description = "I'm a shining command! glistening in LocoMotion!";
        }
	}
}
```
Now to make it run, add a public override void called Execute and if you want arguments, add string[] args.
Heres what we have:
```
using UnityEngine;

namespace Loco.Commands
{
    public class MyCommand : LocoCommand
    {
        public MyCommand()
        {
			CommandName = "mycommand";
            Description = "I'm a shining command! glistening in LocoMotion!";
        }

        public override void Execute(string[] args)
        {
        // add your own logic, this is the log command as an example.
           /* if (args.Length < 1)
            {
                Debug.LogError("Usage: Log \"Your message\"");
                return;
            }

            // Combine all arguments into a single message
            string message = string.Join(" ", args);

            // Remove double quotes around the message
            if (message.StartsWith("\"") && message.EndsWith("\""))
            {
                message = message.Substring(1, message.Length - 2);
            }

            Debug.Log(message);*/
        }
    }
}
```
in this example, we have just taken the code from the log command.
but there you have it you have created your own console command, now load up the game on any scene/map and press the ` key (backquota)
