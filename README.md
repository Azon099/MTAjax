MTAjax
==========
An Ajax-like interface for requesting data from the browser for the MTA Client

### Installation

- Copy and add JQuery to your Resource and HTML file
- Copy mtajax.js and mtajax.lua into the resource
- Embed mtajax.js as Javascript in the HTML Page
- Embed mtajax.lua as clientside script into your resource 

### Usage

After installation you can now use the following Lua functions:
- addAjaxHandler(callname, handler)
- removeAjaxHandler(callname)

### Usage example:  


Lua
````
addAjaxHandler("PlayerMoneyRequest",
	function(playername)
		local player = getPlayerFromName(playername)
		if not player then return false end 
		
		return getPlayerMoney(player)
	end
)
````

Browser
````
mtajax.makeRequest("PlayerMoneyRequest", "sbx320").done(function(data)
{
	if(data === false)
		console.log("Invalid Player")
	else 
		console.log("Player has $" + data[0])
});
````

There's a full example in the example subfolder inside this repository. 