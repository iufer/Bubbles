# Bubbles

A simple plugin for Raphael.js that makes it (relatively) easy to draw circles containing a piece of data and a corresponding label. The example shows how to load these using Google web fonts and some clean simple CSS styles. 

## Requires
* [raphael.js](http://github.com/DmitryBaranovskiy/raphael/raw/master/raphael-min.js)
* [jquery](http://code.google.com/apis/libraries/devguide.html#jquery)

## Usage
Include raphael.makeBubble.js
Edit the bubbleDefaults as needed

	paper = Raphael();
	paper.bubbleDefaults = {
		  		colors:[["#77a6d6","#6a94bf"], ["#f5b034", "#e6a531"], ["#363636","#ffffff"], ["#95d132","#88bf2e"]],
				stroke:4,  // pixel width of the stroke
				speed:90,  // miliseconds between bubble popups
				texts: '#bubbletexts',
				dataClass: 'bubbledata',
				labelClass: 'bubblelabel'
		  	};
		  	
You can change any of these defaults before you call makeBubble(); 
I have provided a default color set. The colors array contains colors in this format: [background color, stroke color]

### Create your first bubble

	<style type="text/css">
		.bubbledata { color:white; font-family:sans-serif; font-weight:800;}
		.bubblelabel { color:white; font-family:sans-serif;}
	</style>	
	
	<div id="bubbletexts" style="position:relative; z-index:10;" ></div>
	<div id="bubbles" style="position:relative; z-index:0;"></div>
	
	<script type="text/javascript">
		var xOrigin = 84, 	// from the left
			yOrigin = 108,  // from the top
			radius = 60,
			colorIndex = 0, // pick the color set from the bubbleDefaults.color array
			animationOrder = 1, // the order that this bubble pops up. you can have multiple bubbles popup at the same time
			dataText = '2,500', 
			labelText = 'People',
			dataClass = 'bigFontClass', 
			labelClass = 'labelFontClass', 
			strong = false;
			
		paper = Raphael(document.getElementById('bubbles'), 300, 300);
		paper.makeBubble(xOrigin, yOrigin, radius, colorIndex, animationOrder, dataText, labelText, dataClass, labelClass, strong);
	</script>
	
Of course you wont have to create all those variables next time you use this, you can plug your data directly into makeBubble() and get going.
dataClass, labelClass, and strong are optional. Using strong will boost the font-size of your data text by 50%, which can be really nice if you are displaying single or double digits.

By default makeBubble will throw all your labels into a box identified in the defaults as "texts". The default id for this box is "bubbletexts". Also a default class will be added to the data text and label text elements. The defaults for these are 'bubbledata' and 'bubblelabel' respectively.

