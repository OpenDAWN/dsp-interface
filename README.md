**Generic DSP Interface**

    npm install dsp-interface

Require this generic, real-time, socketed HTML5 / Touch compatible web socket interface. It returns two arrays, which valaues you can change in your browser.

![pretty generic!](http://i.imgur.com/ix99W.jpg)

**POSTED:** This is a string transporting, float parsing, pseudo midi signal! The GUI is a clumsy, DOM based implementation with non-continunous values! And I traded multi-touch non working range sliders for single touch capable sliders that actually work... so it works on the ipad.

Future version will be nice tho: binary transport, real midi, canvas face, continuous value ranges.

The interface has 10 range sliders, and 8 corresponding exponents buttons.

    var gui = require('dsp-interface');

    gui.start(5001); // optional port, defaults to 8012

    gui.line // a length 10 array
    gui.exp // a length 10 array ([0] and [1] are always zero);

    function(time){
      return Math.sin( time * Math.PI * ( gui.line[3] * Math.pow(10, gui.exp[3]) ))
    }

**You can set your initial values**

    var mui = require('dsp-interface');

    var values = [1,1,-10,1,1,1,1,1,1,1]; // there are 10 range sliders

    var exponents = [0,0,1,1,2,2,3,3,3,3]; // only 8 lines have exponent switches. The first two indecies will always be zero!!!!!!

    mui.start(5001, values, exponents)

**the interface will start at those values**

* Also note: current settings are preserved after refreshing the browser*

**API**

*interface.line*

* line[0] and line[1] return values [0,11] inclusive to correspond with either cranking it past ten, or for 12 octaves for each of the 12 note classes in the western scale. Why 12 octaves? You can't hear 7 hertz, but you can feel it!

* line[2] returns range [-12, 12] inclusive 

* lines 3-9 return values 0-9.9 at intervals of 0.1. 

*interface.exp*

* ui.exp channels all return values 0-3, meant to be used to define the exponent for the their corresponding channels values. exp[0] and exp[1] are always zero.

TODO:

* Add incr / decr buttons to range sliders
* Add on/off punch buttons
* Add placeholders for values you want to come back to