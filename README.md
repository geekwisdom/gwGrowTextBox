# Growing TextBox

![ScreenShot](https://github.com/geekwisdom/gwGrowTextBox/blob/master/assets/growing_example.gif?raw=true | width=100)

## Introducton

One of the trickest problems with HTML and CSS is creating nice textboxes that do not hide text for the user.  If the user wishes to type something in the box, and their is a size limit  (let's say limited 25 characters). The problem is what width to you apply to hold 25 characters?

Depending upon the font choosen, characters can be cut off and display incorrectly to the user when typing or reading the value in the box.

In this example, I present a method of allowing a textbox (input) to grow as needed to always accomodate the text entered regardless of font type or size.

## Design

One key to making this system work lies in the assumption that each textbox itself is within its own div and that the with of the inputbox is limited to the width of this outer div

	<div style="width:200px;">
	Example #1: <input style="width:100%" name="boxexample1" type="text" 	maxlength="50"  id="example1" onkeydown="myWebUI.onGrow(this);"/>
	</div>


## JavaScript


The magic happens within the *onkeydown* event of the inputbox. Each time the user types a character we create another invisible div and place the text content into that div, calculate the exact width needed to display the text just typed

	var gwGetDefaultFontSize=function(pa)
	 {
	 pa= pa || document.body;
	 var who= document.createElement('div');
	 who.style.cssText='display:inline-block; padding:0; line-height:1;position:absolute; visibility:hidden; font-size:1em';
	 who.appendChild(document.createTextNode('a'));
	 pa.appendChild(who);
	 var fs= [who.offsetWidth, who.offsetHeight];
	 pa.removeChild(who);
	 return fs;
 }



The result is a textbox that grows as it needs to such that the entire text as typed by the user is visible at all times.  This idea can be extended as well to set the width as data is loaded or copied/pasted into the box as well using a similar method.   

Enjoy !
