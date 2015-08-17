## HTML / JavaScript ##

Sample HTML site code here represents an example of what a site may look like. Content divs used here are for demonstration purposes. DoubleClick ad tag used here is also for example purposes.

#### Sample Site Script ####

```

<!DOCTYPE html>
<html>
  <head>
    
    <meta charset="utf-8"/>
    <title>IAB Billboard : Flash Branded</title>
    <link type="text/css" rel="stylesheet" href="style/main.css"/>
    
    <script type="text/javascript">
      
      
      // check cookie on page load 
      
      function checkCookie()
      {
        var adstate = getCookie("flashBrandAdState");
        
        if (adstate != null && adstate != "")
        {
          // cookie is already set, adjust state accordingly
          
          setState(adstate);
          
        }
        else 
        {
          // cookie is not set, default to expanded
          
          adstate = "expanded";
          
          setCookie("flashBrandAdState",adstate,1);
          
          setState(adstate);
        }     
      }
      
      // adjust ad state and cookie setting on user click to change state
      
      function setState(state){
        
        var adstate = state;
        
        if(adstate == "expanded"){
          handleExpand();
        } else {
          handleCollapse();
        }
      }
      
      // adjust div sizes and and html depending on state
      
      function handleCollapse(){
        
        setCookie("flashBrandAdState","collapsed",1);
        
        var billboard = document.getElementById("adUnit");
        
        billboard.style.width = "300px";
        billboard.style.height = "31px";
        billboard.style.left = "-670px";
      }
      
      function handleExpand(){
        
        setCookie("flashBrandAdState","expanded",1);
        
        var billboard = document.getElementById("adUnit");
        
        billboard.style.width = "970px";
        billboard.style.height = "250px";
        billboard.style.left = "0px";    
      }
      
      // finding cookie and returning contents
      
      function getCookie(ad_state)
      {
        var i,x,y,ARRcookies=document.cookie.split(";");
        for (i=0;i<ARRcookies.length;i++)
        {
          x=ARRcookies[i].substr(0,ARRcookies[i].indexOf("="));
          y=ARRcookies[i].substr(ARRcookies[i].indexOf("=")+1);
          x=x.replace(/^\s+|\s+$/g,"");
          if (x==ad_state)
          {
            return unescape(y);
          }
        }
      }
      
      // set cookie contents for page display on return until midnight when execution changes
      
      function setCookie(ad_state,value,exdays)
      {
        var date = new Date();
        var midnight = new Date(date.getFullYear(), date.getMonth(), date.getDate(), 23, 59, 59);
        var state_value = escape(value) + ((exdays==null) ? "" : "; expires=" + midnight.toUTCString());
        document.cookie= ad_state + "=" + state_value;
      }
      
      // this function is called from Flash to determine ad state on page load
      
      function getFlashState(){
        var adstate = getCookie("flashBrandAdState");
        
        return adstate;
      }
      
      
      // load contents of ad tag into iframe
      
      function loadBanner(){
        window.frames["banner"].document.open();
        window.frames["banner"].document.write('<script language="JavaScript" src="http://ad.doubleclick.net/adj/iab.demos/_default;sz=970x250;extra_kw=flashbranded" type="text/javascript"><\/script>');
        window.frames["banner"].document.close();
        
        checkCookie();
      }
      
    </script> 
    
  </head>
  <body onload="loadBanner()">
    
    <div id="center">
      
      <div id="contentLogo" class="mockContent"></div>
      
      <div id="contentSearch" class="mockContent"></div>
      
      <div id="adUnit">
        
        <iframe name="banner" id="banner" height="250px" width="970px" frameborder="0"></iframe>
        
      </div>
      
      <div id="contentTop" class="mockContent"></div>
      
      <div id="contentRight" class="mockContent"></div>
      
      <div id="contentLeft" class="mockContent"></div>
      
      <div id="contentBottom" class="mockContent"></div>
      
    </div>
  </body>
</html>

```