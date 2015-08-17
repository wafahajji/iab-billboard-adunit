## HTML / JavaScript ##

Sample HTML site code here represents an example of what a site may look like. Content divs used here are for demonstration purposes. DoubleClick ad tag used here is also for example purposes.

#### Sample Site Script ####

```

<!DOCTYPE html>
<html>
  <head>
    
    <meta charset="utf-8"/>
    <title>IAB Billboard : JS Unbranded</title>
    <link type="text/css" rel="stylesheet" href="style/main.css"/>
    
    <script>
      
      // check cookie on page load 
      
      function checkCookie()
      {
        var adstate = getCookie("jsNoBrandAdState");
        
        if (adstate != null && adstate != "")
        {
          // cookie is already set, adjust state accordingly
          
          setState(adstate);
          
        }
        else 
        {
          // cookie is not set, default to expanded
          
          adstate = "expanded";
          
          setCookie("jsNoBrandAdState",adstate,1);
          
          setState(adstate);
        }     
      }
      
      // adjust ad state and cookie setting on user click to change state
      
      function setState(state){
        
        var adstate = state;
        
        if(adstate == "expanded"){
          handleShow();
        } else {
          handleClose();
        }
      }
      
      // adjust div sizes and and html depending on state and removes iframe with ad tag
      
      function handleClose(){
        var billboard = document.getElementById("adUnit");
        var show = document.getElementById("showButton");
        
        show.innerHTML = '<img src="./images/show_ad.jpg" />';
        show.style.display = "inline";
        show.style.width = "300px";
        show.style.height = "31px";
        billboard.style.display = "none";
        billboard.innerHTML = "";
      }
      
      function handleShow(){
        var billboard = document.getElementById("adUnit");
        var show = document.getElementById("showButton");
        
        show.style.display = "none";
        billboard.style.display = "inline";
        billboard.style.width = "970px";
        billboard.style.height = "250px";
        createFrame();
      }
      
      function createFrame(){
        
        // creating iframe to serve js ad tag
        
        var billboard = document.getElementById("adUnit");
        var iframe = document.createElement('iframe');
        
        iframe.setAttribute('name', 'banner');
        iframe.setAttribute('id', 'banner');
        iframe.setAttribute('height', '250');
        iframe.setAttribute('width', '970');
        iframe.setAttribute('frameborder', '0'); 
        billboard.appendChild(iframe);
        
        loadBanner();      
      }
      
      // load contents of ad tag into iframe
      
      function loadBanner(){
        window.frames["banner"].document.open();
        window.frames["banner"].document.write('<script language="JavaScript" src="http://ad.doubleclick.net/adj/iab.demos/_default;sz=970x250;extra_kw=jsunbranded" type="text/javascript"><\/script>');
        window.frames["banner"].document.close();
      }
      
      // this function will be called from Flash on Expand state and from HTML on show img click
      
      function handleClick(){
        
        // obtain current cookie contents
        
        var adstate = getCookie("jsNoBrandAdState");
        
        // revise cookie contents
        
        if(adstate=="expanded"){
          handleClose();
          setCookie("jsNoBrandAdState","collapsed",1);
        } else {
          handleShow();
          setCookie("jsNoBrandAdState","expanded",1);
        }
        
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
      
    </script> 
    
  </head>
  <body onload="checkCookie()">
    
    <div id="center">
      
      <div id="contentLogo" class="mockContent"></div>
      
      <div id="contentSearch" class="mockContent"></div>
      
      <div id="showButton" onclick="handleClick()"></div>
      
      <div id="adUnit"></div>
      
      <div id="contentTop" class="mockContent"></div>
      
      <div id="contentRight" class="mockContent"></div>
      
      <div id="contentLeft" class="mockContent"></div>
      
      <div id="contentBottom" class="mockContent"></div>
      
    </div>
  </body>
</html>

```