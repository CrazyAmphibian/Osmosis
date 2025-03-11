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
	implications - allows a combination of tags to add or remove other tags


why Osmosis?
	the program is named after reverse-osmisis - a filtering technique.
	much like real-world, reverse-osmosis isn't that efficent
	but, it's incredibly good at filtering - the design of the program.
	unlike other contemporary programs, Osmosis allows incredibly complex filtering via the use of so-called "boolean filters". (see below for more details)
	osmosis can also handle implications, and add tags with little effort.
	additionally, tagging is made faster via the use of the modifier keys shift and conrol (see below for more details)


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
		shift: set input to selected tag (click)
		control: preserve input string
		control+c - copy the image's tags into the clipboard
		control+v - add the clipboard's tags to the current image
		control+shift+c - add the image's tags into the clipboard
		control+shift+v - replace all of the image's tags with the clipboard's
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
	Example: to filter out results matching A unless they also match B:
		NAND
			OR
				A
			NOR
				B
	to remove a boolean filter, remove all of its paired tags, and it will automatically delete.


"implications" view
	rather than using a standard tag implication system, Osmosis uses its powerful "boolean filters" to pair tags together.
	weather it be a simple A implies B, or a more complicated check, the program will correctly apply tags.
	to use the implications screen, it is recomended to fist be familiar with the "boolean filter" system
	not only can implications add tags, it can also remove them, too.

	operating implications:
		each implication has two sets, TRUE and FALSE. the former will fire when the boolean filter condition is true, and fires FALSE if it is not
		clicking on the "add:" part of a tag on the left collum will change it to "sub:", meaning it will remove the tag instead of adding.
		don't worry about tags that are already there or don't exist - the program will not be bothered by it.
		the implications are only ran once you are no longer on the page, so you can take your time to make sure it is correct.


supported platforms: (add as you test)
	windows: tested to work on 64-bit windows 10, but should work on earlier versions and 32 bit as well.
			windows 10: confirmed 64 bit support, 32 bit should work fine
	linux: tested on 64-bit Ubuntu, but should work on other distros.
			debian: confirmed 64-bit support (x86)
				ubuntu: confirmed 64-bit support (x86)
					mint:  confirmed 64-bit support (x86)
	MacOS: does not work, and is not likley able to for lack of hardware to test it on. (feel free to try (main script: OS-specific functions))

building:
	building the program from source is very easy. simply download the source code, then open it into the defold code editor (opening the game.project with it.). once opened, go to the top bar to Project->Bundle, then chose the right platform for your system.
	choose either a debug or release build (debug recomended, has some exclusive features)
	if you do not wish to manually build, executables are released when there is a significant feature disparity.

known issues/notes:
	on windows a firewall popup occurs upon first startup
		this is, from my best guess, because the engine opens a local debug server
		feel free to disable it if it seems spooky, the program makes no network calls on its own
	images are loaded/unloaded into memory as needed, and may cause stutter when scrolling
		- this doesn't have a good solution, as storing image data into memory is costly
	some images fail to load ("invalid argument")
		-thre is no solution, as different setups don't always replicate this behavior. program has been hardened against this to prevent crashes.
	Osmosis uses the Defold game engine. scripts are programmed in Lua. for documentation visit the respective links:
		Lua: https://www.lua.org/docs.html
		Defold: https://defold.com/ref/stable/buffer/

todo:


changelog:
	V34
		Implemented a large behind the scenes rework of code
			result is a cleaner codespace
			increased performance
		Added sorting to the gallery view, by memory order, or alphabetical
		Added option to sort gallery images by tag similarity to another image
		Enhanced the options screen
		Added thumbnail generation
			increases gallery performance and reduced memory use
		changed gallery images to be of a fixed size
		Fixed some input-related bugs
		Reduced overall text size
		Moved some buttons which were previously in the options menu
			Copy selected image -> image screen
			Copy showing images -> gallery screen
	V33
		fixed not being able to click out of full image view
		changed smart search algorithm.
			more performant.
			just as mid.
		Changed smart search setting description
			more accurrate
	V32
		Improved smart search
			weights results by total images and occurances better.
		image view, full mode:
			the image can now be dragged across the screen.
	V31
		improved performance of searching significantly (more than 8x)
		improved boolean tag searching to not include tags already in the bool (tag screen only)
	V30
		fixed bug where renaming images breaks arrow key navigation  (issue #6)
		added "smart search" to to image view.
			attempts to sort tags by how they're paired with other images.
			adjustable strength in the config.
	V29
		added background on tags screen (tags+implications) to make it more clear what level everything is at
		you can now change the filenames of images in the program in the settings menu.
	V28
		copy+pasting tags now supported
		tags no longer saved with explicit indexes, making them easier to edit manually and also marginally reduces storage space.
	V27
		new tag color mode: ends in
		switched version labeling
			fits the more 'rolling release' style of development
	1.3.4
		adjusted size of implications gui nodes
		implication conditions should no longer change position during runtime
		fixed erroneous tag adding when clicking the top bar with a string
	1.3.3
		settings page no longer jumps downwards when scrolling
		reduced size of tag color font in settings menu
			allows for more efficent use of screen space
		tag colors can now be changed in order
		tag colors should keep the same order
			unable to use non-numerical indexes, note if you manually edit the config
		tag colors now have operation modes
			default is starting with, but also has an option for only containing
		a blank tag on the tag screen now functions as a wildcard for all images to allow passthrough
	1.3.2
		added more debug info to setting page
			now shows tag count, showing images, total images, and parsed images
		adjusted implication code
			should result in fewer weird gaps.
		implications can now be named
			viewable while colapsed and expanded
		implication view now has a scroll bar
		fixed some image view issues with varying resolution
			scroll bars and click detection for image
		settings page should work on non-standard resolutions now
	1.3.1
		updated table.tostring function
			now uses the newer version
			config file should be far more readable, and prone to fewer errors
		new option for a fuzzy search
			makes tag searching more lenient at the cost of including more items
	1.3.0
		added ability to pause implications
		fixed click detection on tag screen on larger resolutionss
	1.2.9
		made image view scroll bars more intuitive
		bandaid solution for memory leaks
			garbage collector will be ran every 20 seconds
	1.2.8
		images now use a seperate function to retrieve just their size. it is >10x faster.
			your config image loading count can be increased a lot more with less performance impact.
		image view is less janky with zooming and positioning
		image view now has 2 scroll bars
		implications view now uses a smaller font for the dynamic text to reduce screen usage
		changed the way images are copied
			now uses command line instead of IO library
			should hopefully result in less corruption (issue#3)
	1.2.7
		fixed implications not staying hidden when restarting the program
		implications are no longer removable while hidden
			this is to prevent accidental removal
		added ability to copy the currently selected image into the copied folder
			found in the settings menu
	1.2.6
		fixed an error
		added RAM+CUP use info to settings page (requires that you do a debug build)
		fixed tag filter screen not removing empty booleans
	1.2.5
		fixed error when trying to close full image view
		pressing escape when in full image mode now returns you to regular view, not the gallery
		right clicking a tag in the autofill will set the search text, while not setting the tag. this applies to all applicable screens.
		new image view functionality:
			holding shift while adding a tag makes the input string to longer clear on enter.
			holding control when clicking an autofill tag will preserve the existing input text and still add the tag.
		lowered keypress repeat interval, .2 -> .1
		changed forced image loading so that it actuallly does something
	1.2.4
		fixed tags not applying with the autofill boxes when the inputed text matches an existing tag
	1.2.3
		did not fix tags sometimes not applying
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
