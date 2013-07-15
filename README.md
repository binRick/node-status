# Status!

Makes a little stdout status bar. Currently something I made to use for tooling in node.
Very early/rough stage, changing often.

## An example!
	// Initialize the item with options
	var pizza = status.addItem("pizza", {
	  type: ['bar','percentage'],
	  max: 8
	})
	
	// Increment the item whenever you need it updated
	pizza.inc()
	pizza.inc(3)
	

**Example output:** (More examples in `example.js`)

![image](http://f.cl.ly/items/1O3P0D1g0v1O373u1T1y/animated_status_bar.gif)



## Config
Status accepts the following config options:
+ `invert`: defaults to *true*.
+ `interval`: defaults to 250. Number of milliseconds per re-draw interval.

	status.config({
		invert: false, 
		interval: 200
	})

## Options

All options are optional.

+ `type`: defaults to 'count'. Accepts a single type, or an array of types:
	+ `function(item){ retun item.count }`: specify a type as a custom function to process
	+ `count`: displays the current count. Will display count/max if max is specified.
	+ `bar`: displays a progress bar of ten segments. Only displays if `max` is set.
	+ `percentage`: displays a percentage to 2 decimals. Only displays if `max` is set. Precision can be set manually.
	+ `time`: displays the current time since the application started.
+ `label`: defaults to item name. The label that precedes the count/status.
+ `count`: defaults to 0 (zero). Can specify a starting count.
+ `max`: Will cause 'count' type to display as \<count>/\<max>. ***Required*** for some types.
+ `color`: Status uses [Color](https://github.com/Marak/colors.js) to colorize labels. Specifiy colors as strings.
+ `precision`: defaults to 2. The precision used in percentages.



## Console.log alongside status
Right now, if you have to use `console.log` after the status bar has started, it can be a bit janky because the stdout line isn't cleared when a console.log is run.

You can utilize an extended console.log by adding this after requiring status.

	console = status.console()


## Todo's
+ Add an option to have the bar always at the bottom of the terminal window or just at the bottom of the current page