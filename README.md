# Ashes-f2-trading-system

A trading system just like in fallout 2? IN MY ASHES?!

![Trading interface](trading-ui.png)

## To implement it into your project

 1. Put everything from the `GameInfo` section into the `GameInfo` section of your mod's `MAPINFO` lump.
 2. Put ```#include "zscript/AshesTradingSystem.zc"``` into `ZSCRIPT.ZC`. Don't forget to put `AshesTradingSystem.zc` `into zscript/`-folder of your mod.
 3. Put everything that's left from every folder into the corresponding folder of your mod.
 
OR just use mod launcher and launch this archive as a .pk3 with your mod.


## How to use:
 1. Describe all tradeable items in TRADEITEMS lump like this:

		cls | name | description | price | icon

 for example:
		 
		policepistol | Police Pistol | Standard sidearm. | 120 | 590GA0
		chips | Chips | Trade currency. | 1 | SEL1D0
		batteryreload | Batteries | A small power source for various devices. | 10 | IBTYA0
	 
 2. Describe shops in TRADERS lump, like this:

		trader <unique_shop_key>, <greed_modifier(optional)>
		{
		 <item1_cls>, <amount>, <custom_price(optional)>
		 <item2_cls>, <amount> 
		}

 for example:

		trader Vance
		{
			policepistol, 1, 99 // look, custom price!
			ninemilammo, 20
			shotgunammo, 10
			chips, 250
			FoodTin1, 6
		}
		
		trader Jimmy, 1.2 // all prices are 20% higher, cause <greed_modifier> is 1.2
		{
			chips, 160
			XBowAmmo, 32
			batteryreload, 30
			firstaid, 4
			policepistol, 1, 111 // custom price again
			pipebomb, 2
			thumperammo, 1, 99 // and again
		}
 3. In your conversations, put [trade <unique_shop_key>] into your character's reply where you want to start trading.
	
 for example:
	in LANGUAGE lump - TXT_WALKER_207 = "Let me see what you have. [trade Vance]";
 
 The "[-]" tag is not displayed by the dialog - you'll see only "Let me see what you have.".
 Choosing this reply will forcefully interrupt the coversation and open trade interface, loading "Vance" shop.
 
Refer to TRADERS and TRADEITEMS lumps for detailed information.

Have fun.
