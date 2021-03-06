# Pack
Compress, decompress, and obfuscate table data with Defold

## Installation
You can use Pack in your own project by adding this project as a [Defold library dependency](http://www.defold.com/manuals/libraries/). Open your game.project file and in the dependencies field under project add:

	https://github.com/subsoap/pack/archive/master.zip

Once added, you must require the main Lua module in scripts via

```
local pack = require("pack.pack")
```

## Usage

```
	pack.set_obfuscation_key("my_secret_key")
	pack.set_obfuscation_flag(true)
	
	--- Obfuscate Text
	
	thing_1 = "DEFOLD"
	thing_2 = pack.obfuscate(thing_1)
	thing_3 = pack.obfuscate(thing_2)
	print(thing_3)
	
	text = thing_1
	text = text .. "\n" .. thing_2
	text = text .. "\n" .. thing_3
	
	gui.set_text(gui.get_node("text"), text)

	--- Compress / Decompress Tables
	
	my_table = {text = "this is text"}
	pprint(my_table)
	my_table_2 = pack.compress(my_table)
	pprint(my_table_2)
	my_table_3 = pack.decompress(my_table_2)
	pprint(my_table_3)
```