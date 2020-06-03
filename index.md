# The gowasteland API

GoWasteland uses Lua for its scripting environment. The API outlines how to work with the game itself, cells, entities and most importantly, mods. Game behaviour is encapsulated within mods, each mod registered contains cells, entities and environment definitions.

# File structure
Any code within scripts/config/setup.lua will be executed on startup, meaning you will most likely have to place some code in here.

# Mods

To get started, first register a new mod, be sure to choose a suitable name, description and a version number.

    game:registerMod({  
	    id = "default",  
	    description = "the default behaviour of gowasteland",  
	    version = "0.0.1"  
    })

After registering your mod, any ID you use will need to register the mod it belongs to e.g. **goblin:default**

To view the active mods in the game, access the games mods table from anywhere in your Lua code

    print(game:mods())

# Environments

Once you have registered a mod, you may want to create some custom environments. Just like with mods, environments need registering (Remember, IDs must specify the mod that you want your behaviour to be linked to).

    game:registerEnv({  
	    id = "default:wasteland",  
	    behaviour = "scripts/world/environments/wasteland.lua"  
	})

The behaviour is the location of the script you wish to define the environment behaviour in. In this example we create a file called wasteland.lua (this file can be named anything and located in any directory accessible by the game).

## Spawning Entities
When spawning entities you first specity the ID of the entity, then the tag, then the position. The tag can be anything, it is used to uniquely identify a particular entity in the game.

    environment:spawnEntity("default:player", "player", Vec.new(0,0))


