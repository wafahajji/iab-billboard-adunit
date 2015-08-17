## ActionScript 3 ##

Flash was broken up into two separate files. The parent file acts as the main loader which communcates with the child as well as the JavaScript on the page. The child file acts as the full Billboard creative. Flash is depending on certain elements within the FLA files (i.e. DoubleClick components, etc.)


#### Parent File ####

```

import com.doubleclick.studio.Enabler; 
import flash.external.ExternalInterface;
import flash.events.MouseEvent;

Enabler.init(stage);

close_mc.buttonMode = true;
close_mc.useHandCursor = true;

close_mc.addEventListener(MouseEvent.CLICK, closeBillboard);

function closeBillboard(e:MouseEvent):void {
	
	trace("JavaScript will close at this point.");
	
	ExternalInterface.call("handleClick()");
};

stop();

```

#### Child File : Full Billboard Creative ####

```

import com.doubleclick.studio.proxy.Enabler;
import flash.external.ExternalInterface;
import flash.events.MouseEvent;

close_mc.buttonMode = true;
close_mc.useHandCursor = true;

close_mc.addEventListener(MouseEvent.CLICK, closeBillboard);

function closeBillboard(e:MouseEvent):void {
	
	trace("JavaScript will close at this point.");
	
	ExternalInterface.call("handleClick()");
};

stop();

```