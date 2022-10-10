Welcome to Osmosis - an image tagging program.


How to use:
	first you will need images to filter. place these into the 'images' folder.
	if such folder does not exist, the program will create it upon startup.
	start Osmosis using the exe (on windows) or the x86_64 (on linux).
	you will be met with the 'gallery view' upon startup.
	follow controls listed below to navigate


screens and what they do:
	gallery - shows all the images currently loaded.
	image - a single image display where you can add/remove tags.
	tags - the screen where you set your filters for images based on tags
	settings - user prefences such as tag colors or gui scale


why Osmosis?
	the program is named after reverse-osmisis - a filtering technique.
	much like real-world, reverse-osmosis isn't that efficent
	but, it's incredibly good at filtering - the design of the program.
	unlike other contemporary programs, Osmosis allows incredibly complex filtering via the use of so-called "boolean filters". (see below for more details)


controls:
	general:
		tab: sidebar
		arrow keys: change screen (in sidebar)
	gallery view:	
		left click: select image and go to its page
		scroll wheel: scroll images up/down.
	image view:		
		left click: get full-resolution mode for an image
		right click: remove tag 
		enter: confirm tag entry
		scroll: scroll the image tags
		arrow keys: go to next/previous image
	image view (full size mode):
		left click: return to regular view mode
		scroll: scroll up/down
		shift+scroll: scroll left/right
		ctrl+scroll: zoom in/out
	tag filtering view:
		right click: negate "boolean filters"
		left click: cycle "boolean filters"
		right click: remove tag
		scroll: scroll up/down
		scroll+shift: scroll left/right
	implications view:
		right click: remove tag
		right click: negate boolean
		left click: cycle boolean
		scroll: scroll up/down


"boolean filters":
	instead of using static catagories for filtering, the program is able to dynamically add them by use of the 'tag' screen.
	to add a new boolean filter, navigate to the 'tag' screen, then click the proper button (a vertical line splitting into 2 arrows facing right).
	by default, all tags are surrounded by an "and" filter which is not editable.

	the filters, and how they work:
		all filters operate on a vage boolean logic for how they filter, and each has it's negative operation.

		AND - all tags to be met for an image to show
		OR - at least 1 tag to be met for an image eto show
		XOR -requires at least 1 tag to be met, but not all of them.
		NAND - that all tags are not met (0 tags works, too)
		NOR - none of the tags being met to show (like NOT in other programs)
		NXOR - that either all or none of the tags be met to show 
	the filters can also be nested, to allow for an infinitely customizable filtering.
	to remove a boolean filter, remove all of its paired tags, and it will automatically delete.


"implications" view
	rather than using a standard tag implication system, Osmosis uses its powerful "boolean filters" to pair tags together.
	weather it be a simple A implies B, or a more complicated check, tags will be paired flawlessly. 
	to use the implications screen, it is recomended to fist be familiar with the "boolean filter" system
	not only can implications add tags, it can also remove them, too.

	operating implications:
		each implication has two sets, TRUE and FALSE. the former will fire when the boolean filter condition is true, and fires FALSE if it is not
		clicking on the "add:" part of a tag on the left collum will change it to "sub:", meaning it will remove the tag instead of adding.
		don't worry about tags that are already there or don't exist - the program will not be bothered by it.
		the implications are only ran once you are no longer on the page, so you can take your time to make sure it is correct.


supported platforms:
	windows: tested to work on 64-bit windows 10, but should work on earlier versions and 32 bit as well.
	linux: tested on 64-bit Ubuntu, but should work on other distros.
	MacOS: does not work, and is not likley able to for lack of hardware to test it on. (feel free to try (main script: OS-specific functions))

building:
	building the program from source is very easy. simply download the source code, then open it into the defold code editor (opening the game.project with it.). once opened, go to the top bar to Project->Bundle, then chose the right platform for your system.
	if you do not wish to manually build, executables are released when there is a significant feature disparity

known issues/notes:
	images are loaded/unloaded into memory as needed, and may cause stutter when scrolling
		- this doesn't have a good solution, as storing image data into memory is costly
	images are not initialized at startup (too long), and may result in flashes of color when scrolling quickly when program has just started
		- again, no good solution. you can increase "image loading count" in settings to offset this.
	some images fail to load ("invalid argument")
		-thre is no solution, as different setups don't always replicate this behavior. program has been hardened against this to prevent crashes.
	Osmosis uses the Defold game engine. scripts are programmed in Lua. for documentation visit the respective links:
		Lua: https://www.lua.org/docs.html
		Defold: https://defold.com/ref/stable/buffer/

todo:


changelog:
	1.2.3
		fixed tags sometimes not applying, probably
		improved click detection
		implications screen tags should appear more consistently
		implications can now be collapsed
	1.2.2
		probably fixed the >128 images issue, i hope
	1.2.1
		fixed settings click detection issues
	1.2
		includes previous versions
	1.1.3
		added tag implication
			accesable in a new menu with tab
		added a double and 1.5 size font for less blurry visuals
		added new option: keep images loaded
			when enabled, this will stop images from being unloaded. this makes stuff faster at the cost of higher memory usage. much higher.
		when a config fails to load it now creates a backup before removing
		new copy images feature avalible in settings. new folder to go with it
	1.1.2
		improved click interaction with adding tags on an image
		tags are now sorted by count when adding them
		made the tag filter screen use the better find algorithm
	1.1.1
		hitting escape while adding tags to an image no longer returns you to the gallery
		hitting enter no longer boots you out of the tag adding tab for images
	1.1
		includes previous updates
	1.0.6
		fixed erroring on the image tag adding when inputting a ( or [
	1.0.5
		fixed bug caused by 1.0.4 involving full image view swapping.

	1.0.4
		no longer continuously reloads image data on image view.
		added safeguards for loading unloaded images.
			seeking to fix in the future. happens because only being in gallery view loads image data.

	1.0.3
		changing images now resets the scroll position of tags
		you now have to click the image to swap to full screen view and not to the right of tags

	1.0.2
		added arrow key controls to navigate to the next/previous image in the image view mode 

	1.0.1
		added horizontal scrolling in tag screen

	1.0
		initial release
