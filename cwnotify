// ==UserScript==
// @name         CWNotify
// @namespace    http://tampermonkey.net/
// @version      0.1
// @require
// @description  Notify via Desktop Notifications that there is a Call waiting in our Cisco Queue
// @author       joshwren
// @match       *://*/*
// @grant        none
// ==/UserScript==


function runScriptChecker() {
    var result = $('#LiveDataReport0').find('#dijit18_GridManager_0').find('.dgrid-scroller').find('td.currentWaitingCalls').eq(0).text().trim();
    if (result !=='0' &&result!='') {
         notifyMe();
    }
}



function notifyMe() {
  // Check if the browser supports notifications
  if (!("Notification" in window)) {
    alert("This browser does not support desktop notification");
  }

  // Check if the user is okay to get some notification
  else if (Notification.permission === "granted") {
    // If it's okay let's create a notification
      var options = { icon: 'https://pbs.twimg.com/profile_images/913360333833506816/Y_10CXEI_400x400.jpg'};
    var notification = new Notification("There is a Call Waiting!", options);
  }

  // Otherwise, we need to ask the user for permission
  // Note, Chrome does not implement the permission static property
  // So we have to check for NOT 'denied' instead of 'default'
  else if (Notification.permission !== 'denied') {
    Notification.requestPermission(function (permission) {

      // Whatever the user answers, we make sure we store the information
      if(!('permission' in Notification)) {
        Notification.permission = permission;
      }

      // If the user is okay, let's create a notification
      if (permission === "granted") {
        var notification = new Notification("Hi there!");
      }
    });
  } else {

  }
}

setTimeout(function() {
    setInterval(function() {runScriptChecker();}, 2000);
}, 2000);



