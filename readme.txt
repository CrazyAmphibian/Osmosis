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



supported platforms:
	windows: tested to work on 64-bit windows 10, but should work on earlier versions and 32 bit as well.
	linux: tested on 64-bit Ubuntu, but should work on other distros.
	MacOS: does not work, and is not likley able to for lack of hardware to test it on. (feel free to try (main script: OS-specific functions))


known issues/notes:
	images are loaded/unloaded into memory as needed, and may cause stutter when scrolling
		- this doesn't have a good solution, as storing image data into memory is costly
	images are not initialized at startup (too long), and may result in flashes of color when scrolling quickly when program has just started
		- again, no good solution. you can increase "image loading count" in settings to offset this.
	some images fail to load ("invalid argument")
		-thre is no solution, as diffrent setups don't always replicate this behavior. program has been hardened against this to prevent crashes.
	Osmosis uses the Defold game engine. scripts are programmed in Lua. for documentation visit the respective links:
		Lua: https://www.lua.org/docs.html
		Defold: https://defold.com/ref/stable/buffer/

todo:
	


changelog:
	1.0.5
		fixed bug caused by 1.0.4 involving full image view swapping.

	1.0.4
		no longer continuosuly reloads image data on image view.
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
