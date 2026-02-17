# Documentation
I apologize if this is a bit sloppy or hard to follow, as this is my first time writing documentation for something like this.
Shard is an open-source programming language that you can use to indirectly run Turbowarp blocks. It is related to another project I am working on, TurbOS, that includes a shell and Shard interpreter.
This repository includes documentation for Shard, a TurbOS dev kernel that you can write your own projects ontop of, and some example Shard programs that you can run.

## Rules
I am fine with you using my TurbOS dev kernel, as long as you:
- Credit me for making the dev kernel.
- Give credit to anyone else who's work you may have used, including Turbowarp extensions.
- Keep the initialization screen untouched (with the exception of adding your own logo in the middle, which I am okay with).
- Follow the rules of the GPL v3.0 License. (if you don't know the rules of this license, then please do not use my work until you do).
- Avoid making anything that could be considered NSFW.

# Shard
Below is the documentation for Shard and it's features
Note: In TurbOS, the console can be opened by pressing the open console keybind. By default, this is set to be the ctrl key, but expect it to be different depending on the software you are using.
## Commands
The function and usage of all commands.
### Utility
General-purpose utility commands.
#### Print
Functions the same way as it would function in most other languages, except it doesn't take variables as inputs. Prints the given text to the console.
Usage:
`print [the text you want to print]`
#### Wait
Pauses all operations for a certain number of seconds.
Usage:
`wait (time in secs)`
#### JSeval
Runs JavaScript code that you give it.
This unfortunately is not functional, since the JavaScript extension I am using crashes Turbowarp instead of running the code.
Usage:
`jseval [code]`
#### Noop
Does nothing. This takes no inputs and does nothing with them. There is literally no code attached to this and the shell runs nothing when this command is ran.
Usage:
`noop`
#### Logempty
Clears the console and then outputs the the number of lines that were cleared. This output can be hidden optionally typing `true` as an argument.
Usage:
`logempty <true/false>`
#### Close
Closes the console.
Usage:
`close`
### Data
Data management commands.
#### Set
Sets a given variable to a given value.
Usage:
`set (variable) (value)`
#### krget
Gets the value of a kernel registry entry and outputs it to a given variable.
The kernel registry holds data about the kernel and the project itself.
Usage:
`krget (entry #) (output variable)`
#### orget
Gets the value of a op registry entry and outputs it to a given variable.
The op registry holds the output of certain commands and is currently unused.
Usage:
`orget (entry #) (output variable)`
### Programs
Commands relating to Shard programs.
#### Import
Imports a .shard file from the host OS and places the contents in a new rxFS file at the given location in rxFS. Note that this command always places data into the "/user/" directory and the top level and the result is that you can only import files into directories inside of the /user/ directory, which is intended behavior.
`import (output directory)`
#### Run
Executes a Shard program from the specified rxFS directory. Shard programs can be placed into rxFS using the import command.
Note that this command allows the execution of Shard programs that are outside of the /user/ directory to allow for developers to place Shard programs into other directories and run them in Shard without having to modify the command.
Usage:
`run (exact location of program file)`
#### JumpIf
This command is only able to function properly if it is part of a Shard program. The usage will be explained later in the documentation.
#### ScriptEnd
This command denotes the end of a Shard program. It can be used to end the Shard program prematurely or as a failsafe in case it keeps going after its intended end, which should never happen, but still. This command is only able to function at all if it is part of a Shard program.
Usage:
`scriptend`
### Iframe commands
Commands that interact with Iframes.
#### Open
Opens an Iframe to the specified URL.
Usage:
`ifr.open (URL)`
#### Close
Closes any Iframe.
Usage:
`ifr.close`
#### Send
This triggers the block that sends a message to an opened Iframe. I am not quite sure what this block actually does, and I added it to provide commands for more blocks in the Iframe extension I am using. It exists, though.
Usage:
`ifr.send [message to send to Iframe]`
### CloudLink commands
Commands that interact with CloudLink V4.
#### Connect
Connects to server 7. You can optionally specify a specific websocket URL to connect to instead.
Usage:
`cl.connect (URL (optional))`
#### Disconnect
Disconnects from CloudLink.
Usage:
`cl.disconnect`
#### Uname
Sets a CloudLink username to use. To connect to rooms in CloudLink, you must have a set username.
Usage:
`cl.uname (username)`
#### Room
Links to the specified room ID. Multiple IDs can be specified. If no IDs are specified, will unlink from all rooms.
`cl.room (room ID) (room ID) (room ID)...`
#### Listen
Toggles listening mode, where the shell will output received CloudLink messages from any linked rooms, in plain text, to the console.
#### Send
Sends a given message to all linked rooms.
Usage:
`cl.send [message that you want to send]`
#### Info
Outputs a bunch of information about the current CloudLink status to the console.
Usage:
`cl.info`
