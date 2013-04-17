bottom panel
============

Module for firefox addon sdk to add content to a panel below the main window.

If you want to show some content, but want more space or for your content to be persistent, then the addon sdk Panel module is a bit limiting.

This module creates a new panel below the main window. You can fill this with content like you would a popup panel.

Use it something like this:


    BottomPanel = require("./bottom_panel.js");
    
    bottomPanel = BottomPanel.BottomPanel({
      contentURL: data.url("feed.html"),
      height: "470px",
    }); 
    
    // then you can do things like...
    
    bottomPanel.show();
    
    bottomPanel.port.on("command", function(msg) {
      console.log(msg);
    });
    
    bottomPanel.iframe.addEventListener("load", function(e) {
      bottomPanel.port.emit("some-command");
    }, true);
    
    // and later:
    
    bottomPanel.hide();
    
    

The source code is pretty short and you should be able to extend this pretty easily.
