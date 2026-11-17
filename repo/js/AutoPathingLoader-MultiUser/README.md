# 1. Key Script Configuration and Route Selection

- **Notes:**
	1. The script can only be used after strictly following the configuration steps below; otherwise it will **fail to run** (you can also refer to the log in the bottom-left corner to confirm your next step).
	
	2. Selected routes must meet basic criteria: high reliability (avoiding getting stuck, difficult terrain, or overpowering enemies).

- **Configuration Steps:**
	
	When running without prior configuration, the bottom-left log will display: `Please manually add route folders into the assets/pathing folder and rerun...`, indicating that you need to perform the following:
	
	1. Copy your route folder (which should contain only `.json` pathing files) into the `assets/pathing` directory.
	
	2. Make sure the Paimon menu icon is visible in the top-left corner of Genshin Impact. Run the script directly in the **Scheduler**. When the bottom-left log shows `JS script configuration updated, please reselect route...`, the JS script has loaded the route folders from the previous step, and the script should now have **finished running**.
	
	3. In the **Scheduler**, right-click the script, select **"Edit JS Script Custom Configuration"**, select the route you want to run, and configure all JS settings (the option **Route Settings - Select Route Folder to Execute** will now list your newly added folder name).
	
	4. This step differs depending on your chosen world joining mode:
	
		1. Manual World Joining:
	 
			Ensure you are already in **Co-Op Mode**. Run the script; the script will send verification messages in the chat box, indicating normal operation.
		
		2. Auto World Joining:
		
			Ensure you are in **Single Player Mode**. Run the script; it will automatically wait for members to join (if Host) or request to join the Host's world (if Member), indicating normal operation.

- **Adding More Routes:**
	
	To add more route files, repeat **Configuration Steps** `1-4` above to add new route folders (folder names must be unique).
	
	After adding, choose the corresponding route in the **Select Route Folder to Execute** dropdown in **JS Script Custom Configuration**.

# 2. JS Script Custom Configuration Guide

- **Select World Joining Method**
 
	1. Auto World Joining [Recommended]
		
		When selecting this option, configure the three settings under `Auto World Joining`.
	
	2. Manual World Joining
	
		When selecting this option, configure the settings under `Manual World Joining`.

- **Manual World Joining - Select Your Player Index:**
 
	In manual Co-Op mode, specify your player index (1P / 2P / 3P / 4P) after all players have joined the world.

- **Manual World Joining - Select Total Player Count:**
 
	In manual Co-Op mode, specify the total player count after everyone has joined the world.

- **Auto World Joining - Select Your Role:**
 
	In auto mode, choose whether you are the Host (Leader) or Member (only one Leader can exist; selecting multiple will cause errors).

- **Auto World Joining - Text Input Field**
 
	1. As Host:
	
		Enter the in-game nicknames of all players joining your world (order does not matter), separated by a single space.
	
	2. As Member:
	
		Enter the UID of the world Host (Leader) you want to join.

- **Auto World Joining - Name Matching Mode:**
 
	In auto mode, the matching strategy used to verify player names (Host only):
	
	1. Exact Match (enter player's full nickname):
	
		Matches the full player nickname; best when player nicknames are clearly recognized by OCR.
	
	2. Partial Match (enter easily recognizable continuous text from the nickname):
	
		Matches partial text contained in the player nickname; best when full nicknames are difficult for OCR to parse reliably.
 
- **Route Settings - Select Route Folder to Execute**
 
	This dropdown will be empty on initial launch. See section `1. Key Script Configuration and Route Selection` above for setup instructions.

# 3. Precautions / Notes

All players must use **completely identical** route folders and contents; otherwise verification will fail and terminate the script.

- **Route Folder Location:** `assets/pathing`

	For example, if you have a folder named `DeathNote-400` containing several `.json` path files, copy `DeathNote-400` into `assets/pathing`.
	
- **Directory Structure:** `assets/pathing/<Your_Route_Folder>/<route_files>.json...`
 
	The `assets/pathing` folder must only contain folders; placing loose files directly here is invalid.
	
	Route subfolders under `assets/pathing` must only contain `.json` files.

- **Built-in Routes in assets/pathing:**
	
	Pre-packaged routes are already tested and adapted for Co-Op mode and can be used immediately.

# 4. Use Cases

- **Synchronized Map Tracking Across Multiple Accounts:**
 
	Theoretically, all map tracking route files can be executed synchronously in Co-Op.

- **Dual-Instance Setup on a Single PC:**
 
	Run two instances of Genshin Impact + BetterGI on one machine to double mob farming efficiency. For example, configure both accounts in the Scheduler: one acts as Host then Member, while the other acts as Member then Host, automatically farming both worlds consecutively.
	
- **Co-Op Mob Farming with Other BetterGI Users:**
 
	Coordinate with other BetterGI users, import the same route files, and farm together in 2–4 player Co-Op (route progress remains synchronized, ensuring all players receive identical loot).
