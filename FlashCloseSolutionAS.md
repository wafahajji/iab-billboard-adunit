## ActionScript 3 ##

Flash was broken up into three separate files. The parent file acts as the main loader which communcates with the children as well as the JavaScript on the page. Two child files exist : collapsed version which contains show button creative and another with full Billboard creative. Flash is depending on certain elements within the FLA files (i.e. DoubleClick components, etc.)


#### Parent File ####

```

import com.doubleclick.studio.Enabler;
import com.doubleclick.studio.events.StudioEvent;
import com.doubleclick.studio.expanding.ExpandingComponent;
import com.doubleclick.studio.display.StudioLoader;
import flash.external.ExternalInterface;
import flash.events.MouseEvent;
import flash.net.URLRequest;

Enabler.init(stage);

var myCollapse:StudioLoader = new StudioLoader();
var reqCol:URLRequest = new URLRequest("sample_billboard_child_button_as3.swf");

var myExpand:StudioLoader = new StudioLoader();
var reqExp:URLRequest = new URLRequest("sample_billboard_child_ad_as3.swf");

function serveUnit():void
{
	var adstate:String = String(ExternalInterface.call("getFlashState"));

	switch (adstate)
	{
		case "expanded" :
			ExpandingComponent.expand();
			updateStatus();

			break;
		case "collapsed" :
			collapseUnit();
			updateStatus();
			
			break;
		default :
			ExpandingComponent.expand();
			updateStatus();
			
			break;
	}
}

function expandUnit():void
{
	ExternalInterface.call("handleExpand");

	myExpand.load(reqExp);
	child_ad_mc.addChild(myExpand);
	
	if (child_button_mc != null && contains(myCollapse)) {
		
		child_button_mc.removeChild(myCollapse);
	
	}
	
	updateStatus();
}

function collapseUnit():void
{
	ExternalInterface.call("handleCollapse");
	
	myCollapse.load(reqCol);
	child_button_mc.addChild(myCollapse);
	
	if (child_ad_mc != null && contains(myExpand)) {
		
		child_ad_mc.removeChild(myExpand);
	
	}
	
	updateStatus();
}

function updateStatus():void
{
	var adstate:String = String(ExternalInterface.call("getFlashState"));
	status_txt.text = adstate;
}

stop();

```

#### Child File : Button Creative ####

```

import com.doubleclick.studio.proxy.Enabler;
import com.doubleclick.studio.expanding.ExpandingComponent;
import flash.events.MouseEvent;

show_mc.buttonMode = true;
show_mc.useHandCursor = true;

show_mc.addEventListener(MouseEvent.CLICK, showBillboard);

function showBillboard(e:MouseEvent):void
{
	ExpandingComponent.expand();
}

stop();

```

#### Child File : Full Billboard Creative ####

```

import com.doubleclick.studio.proxy.Enabler;
import com.doubleclick.studio.expanding.ExpandingComponent;
import flash.events.MouseEvent;

close_mc.buttonMode = true;
close_mc.useHandCursor = true;

close_mc.addEventListener(MouseEvent.CLICK, closeBillboard);

function closeBillboard(e:MouseEvent):void
{
	ExpandingComponent.collapse();
}

stop();

```