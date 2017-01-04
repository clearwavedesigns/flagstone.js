# FlagstoneJS
## Dynamic &#38; responsive tiling

[Demo](http://codepen.io/depthdev/pen/pNMOdd)

<a href="http://codepen.io/depthdev/full/pNMOdd/" target="_blank"><img src="http://cdn.depthdev.com/flagstone-3.2.0-screenshot.png"></a>

## Docs

### Download the ES5 minified version, or ES6 expanded version.

---

### Hide the content
For instances with large amounts of "stones," it's recommended that you hard code this attribute and style: `style="visibility:hidden;"`.

---

### Instantiate 1 or more Flagstone instances
NOTE: Calling `flagstone()` returns a new Flagstone instance.

`const fs = flagstone(); // Requires the wrapper element to have a class of ".flagstone" on it.`

OR

`const fs = flagstone(document.getElementsByTagName('article')[1]); // Pass in the element to bootstrap`

OR

<sub>
**const fs = flagstone({**  
  &#160;&#160;&#160;&#160;**elem:** document.getElementsByTagName('article')[0], *// Wrapping element*  
  &#160;&#160;&#160;&#160;**bedPadding:** 10, *// The padding around the area edge*  
  &#160;&#160;&#160;&#160;**stonesMargin:** 10, *// Margin between stones*  
  &#160;&#160;&#160;&#160;**margin:** 10, *// This overrides bedPadding &#38; stonesMargin and is equivalent to setting them both to this value*  
  &#160;&#160;&#160;&#160;**minWidth:** 280, *// Minimum width you want an element to be*  
  &#160;&#160;&#160;&#160;**maxColumns:** 5, *// Maximum number of columns to display*  
  &#160;&#160;&#160;&#160;**direction:** 'left', *// Alternative is "right"*  
  &#160;&#160;&#160;&#160;**random:** false, *// Display stones in a random order*  
  &#160;&#160;&#160;&#160;**square:** false, *// Makes each flagstone square*  
  &#160;&#160;&#160;&#160;**space:** false, *// Spaces out stones randomly*  
  &#160;&#160;&#160;&#160;**spaceFrequency:** 0.4, *// Adjusts the frequency of the amount of spaces (as a float 0.0 - 1.0)*  
  &#160;&#160;&#160;&#160;**animationDuration:** 0, *// Animation duration (milliseconds)*  
  &#160;&#160;&#160;&#160;**animationTimingFunction:** 'linear', *// CSS animation timing function as a string*  
  &#160;&#160;&#160;&#160;**resizeDelay:** 250, *// Delay to run resize/reset function after resizing the window (milliseconds)*  
  &#160;&#160;&#160;&#160;**imagesLoadedQueryDuration:** 2500, *// Duration to check for images that have finished loading after instantiation (milliseconds).*  
  &#160;&#160;&#160;&#160;**imagesLoadedQueryFrequency:** 100, *// Frequency to check for images that have loaded within the imagesLoadedQueryDuration (milliseconds)*  
  &#160;&#160;&#160;&#160;**dragAndDrop:** false, *// Enable drag n' drop*  
  &#160;&#160;&#160;&#160;**dragAndDropAutoDelay:** 1000, *// Enable automatic/previewing drag n' drop by setting a delay (milliseconds)*  
  &#160;&#160;&#160;&#160;**eventResetDelay:** 0, *// Delay to call reset when an element with the "flagstone-reset" class is triggered (important when resizing CSS animations are used)*  
  &#160;&#160;&#160;&#160;**eventResizeDuration:** 250, *// Animation duration when an element with the "flagstone-resize" class is triggered (important when resizing CSS animations are used and you don't want a reset to be called)*  
  &#160;&#160;&#160;&#160;**callback:** function(elem, index) {} *// Callback to run against every element every time a soft reset is called. WARNING: If attaching listeners, you'll need to remove the listeners first to avoid stacks of listeners!*  
**});**
</sub>

---

### METHODS:

#### ADJUST
Allows the developer to provide options to the user to change settings on the fly.  
**fs.adjust({**  
&#160;&#160;&#160;&#160;**margin:** 10,  
&#160;&#160;&#160;&#160;**bedPadding:** 10,  
&#160;&#160;&#160;&#160;**stonesMargin:** 10,  
&#160;&#160;&#160;&#160;**minWidth:** 280,  
&#160;&#160;&#160;&#160;**maxColumns:** 5,  
&#160;&#160;&#160;&#160;**dragAndDrop:** true,  
&#160;&#160;&#160;&#160;**callback:** function(elem, index) {}  
**});**

#### DESTROY
Removes Window resize event listener, and removes the styles from the document head.  
**fs.destroy();**

#### RESET (Soft)
Re-calculates sizes and spacing of existing stones. This is handled automatically on resize, and when an element with a class of `flagstone-reset` is selected.  
**fs.reset();** // Good for adjusting static content.

#### RESET (Hard)
Finds stones anew, adds any applicable listeners, and resets all positions. IMPORTANT: In most cases, this will never be needed as DOM changes are being listened for already and will call this method automatically.  
**fs.hardReset();**

#### HIDE
Hides the flagstone wrapper until re-calculation is complete; great before new content is injected into the DOM. IMPORTANT: Generally speaking, most use cases are handled automatically.  
**fs.hide();**

---

### CLASSES

#### flagstone-remove
Elements with the `flagstone-remove` class on them will cause the stone it's contained within to be removed from the DOM when *clicked*; or, when the *enter* or *space* keys are pressed.

#### flagstone-resize
Elements with the `flagstone-resize` class on them will cause "stones" below it to move with the developer-provided height changes of this targeted stone when *clicked*; or, when the *enter* or *space* keys are pressed.

#### flagstone-reset
Elements with the `flagstone-reset` class on them will trigger a soft reset when *clicked*; or, when the *enter* or *space* keys are pressed.

---

### Other
#### Example styling for drag and drop:
**.flagstone-0-bed.flagstone-dragover {**  
&#160;&#160;&#160;&#160;box-shadow: inset 0 0 4px 4px #fff;  
**}**  
**.flagstone-drag {**  
&#160;&#160;&#160;&#160;filter: grayscale(1) blur(4px);  
&#160;&#160;&#160;&#160;opacity: 0.25;  
**}**  
**.flagstone-left {**  
&#160;&#160;&#160;&#160;box-shadow: -8px 0 4px -4px #fff;  
**}**  
**.flagstone-right {**  
&#160;&#160;&#160;&#160;box-shadow: 8px 0 4px -4px #fff;  
**}**
