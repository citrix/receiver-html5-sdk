# Class: Session

## Session

### new Session()

### Members

### container

Contains the type and value of the container where the session is launched.
### Properties:

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>container</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="description last"> <h6>Properties</h6><table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>type</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Type of the container. Will be set to "iframe" or "window" when launchType is set to "embed" or "newtab" respectively.</td></tr><tr> <td class="name"><code>value</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="description last">Contains the iframe DOM object or reference to the window where the session is launched based on the launchType.</td></tr></tbody></table> </td></tr></tbody></table>
### (readonly) id

### Properties:

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>id</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">ID of the object.</td></tr></tbody></table>

### Methods

### (inner) addListener(eventType, eventListener)

Registers the eventListener on the eventType.
###Parameters:


<table class="params"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>eventType</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Type of the event for which the listener needs to be attached.<br><br>Supported event types : <br><a href="/Session#~event:onConnection">onConnection</a><br><a href="/Session#~event:onConnectionClosed">onConnectionClosed</a><br><a href="/Session#~event:onURLRedirection">onURLRedirection</a><br><a href="/Session#~event:onError">onError</a><br></td></tr><tr> <td class="name"><code>eventListener</code></td><td class="type"> <span class="param-type"><a href="/global#eventListener">eventListener</a></span> </td><td class="description last">Listener to handle the event.</td></tr></tbody></table>

Supported event types : 
onConnection
onConnectionClosed
onURLRedirection
onError
eventListener	eventListener	Listener to handle the event.
### Example

```
// Adding onConnection event handler
function connectionHandler(event){
	console.log("Event Received : " + event.type);
	console.log(event.data);		
}				
sessionObject.addListener("onConnection",connectionHandler);

// Adding onConnectionClosed event handler
function connectionClosedHandler(event){
	console.log("Event Received : " + event.type);		
	console.log(event.data);		
}
sessionObject.addListener("onConnectionClosed",connectionClosedHandler);

// Adding onError event handler
function onErrorHandler(event){
	console.log("Event Received : " + event.type);		
	console.log(event.data);
}
sessionObject.addListener("onError",onErrorHandler);

//Adding onURLRedirection event handler
function onURLRedirectionHandler(event){
	console.log("Event Received : " + event.type);		
	console.log(event.data);
}
sessionObject.addListener("onURLRedirection",onURLRedirectionHandler);
```

### (inner) addToolbarBtns(customToolbarData)

Adds the custom buttons to the in-session toolbar.
### Parameters:

<table class="params"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>bounds</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="description last">Contain session resolution settings.</td></tr></tbody></table>
### Note: Toolbar should be enabled to use this method.

### Properties

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>bounds.autoresize</code></td><td class="type"> <span class="param-type">boolean</span> </td><td class="description last">Should be set to false to give fixed width and height to session. If this value is set to true then the session is resized to match the size of iframe element or the tab.</td></tr><tr> <td class="name"><code>bounds.width</code></td><td class="type"> <span class="param-type">Number</span> </td><td class="description last">Width of the session specified in pixels. This value will be set only when autoresize is set to false.</td></tr><tr> <td class="name"><code>bounds.height</code></td><td class="type"> <span class="param-type">Number</span> </td><td class="description last">Height of the session specified in pixels. This value will be set only when autoresize is set to false.</td></tr></tbody></table>
 

Defaults to true.
config.imageUrl	String	Image url of the button. Mandatory when the button is added to primary toolbar button.

### Note:
Recommendation is to host the images where SDK files are hosted and give full path of the image. 
Other option is to use the data URL of the image.

If the images are hosted in origin other than that of SDK then Content security policy in HDXEngine.html has to be edited to allow the images to be fetched.
config.position	String	Specifies the position of the custom button when added as primary toolbar button.For secondary custom buttons it would be appended to the menu shown on clicking more button.

1) Setting to 'front' would add the button to the front of the toolbar (immediately after receiver button).
2) Setting to 'rear' would add the button before more button.

### Note : For secondary custom buttons it would be appended to the menu shown on clicking more button.

Defaults to 'front' when unspecified.
config.toolTip	String	Value is set as tooltip if the custom button is primary. 
For secondary the value is shown as the menu item.
handler	eventListener	Event listener that listens for the click of the custom toolbar button.
### Example

Example 1 :  Adding help custom button to primary toolbar and position is set to rear(added before more button)

```
function helpButtonHandler(eventObj){
	console.log("Event Received : " + event.type);		
	console.log(event.data);
}

var customToolbarData = [{"id" :"help","config":{"position":"rear","imageUrl":"http://<path_of_the_image>/help.png","toolTip":"Help"},"handler":helpButtonHandler}];
sessionObject.addToolbarBtns(customToolbarData);
```

Example 2 :  Adding back and forward buttons that allows navigation of the webpage in browser and position is set to front (added after receiver button). 

```
function backButtonHandler(eventObj){
	console.log("Event Received : " + event.type);		
	console.log(event.data);
	sessionObject.sendSpecialKeys(["ALT_KEY","LEFT_ARROW"]);
}
function forwardButtonHandler(eventObj){
	console.log("Event Received : " + event.type);		
	console.log(event.data);
	sessionObject.sendSpecialKeys(["ALT_KEY","RIGHT_ARROW"]);
}

var customToolbarData = [];
customToolbarData.push({"id" :"back","config":{"position":"front","imageUrl":"http://<path_of_the_image>/back.png","toolTip":"Back"},"handler":backButtonHandler});
customToolbarData.push({"id" :"forward","config":{"position":"front","imageUrl":"http://<path_of_the_image>/fwd.png","toolTip": "Forward"},"handler":forwardButtonHandler});

sessionObject.addToolbarBtns(customToolbarData);<br/><br/><br/>
```

Example 3 :  Adding help custom button as primary toolbar with position set to rear and contact us button as secondary button.

```
function helpButtonHandler(eventObj){
	console.log("Event Received : " + event.type);		
	console.log(event.data);
}
function contactUsButtonHandler(eventObj){
	console.log("Event Received : " + event.type);		
	console.log(event.data);
}
var customToolbarData = [];
customToolbarData.push({"id" :"help","config":{"position":"rear","imageUrl":"http://<path_of_the_image>/help.png","toolTip":"Help"},"handler":helpButtonHandler});
customToolbarData.push({"id" :"contactUs","config":{"toolTip":"Help","isPrimary":false},"handler":contactUsButtonHandler});

sessionObject.addToolbarBtns(customToolbarData);
```

### (inner) changeResolution(bounds)

Changes the resolution of the session.
### Parameters:

<table class="params"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>bounds</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="description last">Contain session resolution settings.</td></tr></tbody></table>
### Properties:

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>bounds.autoresize</code></td><td class="type"> <span class="param-type">boolean</span> </td><td class="description last">Should be set to false to give fixed width and height to session. If this value is set to true then the session is resized to match the size of iframe element or the tab.</td></tr><tr> <td class="name"><code>bounds.width</code></td><td class="type"> <span class="param-type">Number</span> </td><td class="description last">Width of the session specified in pixels. This value will be set only when autoresize is set to false.</td></tr><tr> <td class="name"><code>bounds.height</code></td><td class="type"> <span class="param-type">Number</span> </td><td class="description last">Height of the session specified in pixels. This value will be set only when autoresize is set to false.</td></tr></tbody></table>
Examples

Example 1 : To change resolution to fixed width and height  
```
var bounds = {
	"autoresize":false,
	"width": "800",
	"height":"600"
}
sessionObject.changeResolution(bounds);
```

Example 2 : To change the session resolution to match the iframe element or tab size   

```
var bounds = {
	"autoresize": true
}
sessionObject.changeResolution(bounds);
```

### (inner) disconnect()

Disconnects the session.
### (inner) logoff()

Sends logoff to the session.
### (inner) removeListener(eventType, eventListener)

Removes the eventListener on the eventType.
### Parameters:

<table class="params"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>eventType</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Type of the event for which the listener needs to be removed.<br><br>Supported event types : <br><a href="/Session#~event:onConnection">onConnection</a><br><a href="/Session#~event:onConnectionClosed">onConnectionClosed</a><br><a href="/Session#~event:onURLRedirection">onURLRedirection</a><br><a href="/Session#~event:onError">onError</a><br></td></tr><tr> <td class="name"><code>eventListener</code></td><td class="type"> <span class="param-type"><a href="/global#eventListener">eventListener</a></span> </td><td class="description last">Listener to handle the event.</td></tr></tbody></table>

Supported event types : 
onConnection
onConnectionClosed
onURLRedirection
onError
eventListener	eventListener	Listener to handle the event.
### Example
```
//Removing the event handler for onConnection event
function connectionHandler(eventObj){
	console.log("Event Received : " + event.type);		
	console.log(event.data);
}
sessionObject.removeListener("onConnection",connectionHandler);
```
### (inner) removeToolbarBtns(toolbarButtonIds)

Removes the custom toolbar buttons added to in-session toolbar.
### Parameters:

### Name	Type	Description
toolbarButtonIds	Array.<String>	Array of custom toolbar button ids to be removed.
Example

Example 1 : Removing the help button added using addToolbarBtns example.
```
sessionObject.removeToolbarBtns(["help"]);
```
Example 2 : Removing multiple buttons say back and forward buttons added using addToolbarBtns example.
```
sessionObject.removeToolbarBtns(["back","forward"]);
```
### (inner) sendSpecialKeys(keys)

Sends a key combination to the session.
### Parameters:

<table class="params"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>keys</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Key combination string.</td></tr></tbody></table>

Till 1.1 version only "ctrl+alt+del" was supported. From 1.2 version, more key combinations can be sent to session.
### Example

Example 1 : Sends Ctrl+alt+delete to the session.
```
var keys = ["Control","Alt","Delete"];
sessionObject.sendSpecialKeys(keys);
```

Example 2 : To preview different apps running inside session, Ctrl+alt+tab can be sent.
```
var keys = ["Control","Alt","Tab"];
sessionObject.sendSpecialKeys(keys);
```
				
### (inner) start(launchData)

Starts the session.
### Parameters:

<table class="params"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>launchData</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="description last">Contains the type and value of ICA.</td></tr></tbody></table>
### Properties:

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>launchData.type</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Specifies the data type of ICA data. Allowed values are "json" or "ini".</td></tr><tr> <td class="name"><code>launchData.value</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">ICA data to start the session. It should be a JSON object when type is "json" or a string read from a .ini file when type is "ini".</td></tr></tbody></table>
### Examples

Example 1 : When ICA data is in JSON format                                
```
var icaObj = {
	"ClientName":"HTML5-Receiver",
	"Domain":"<domain_name>",
	"ClearPassword":"<password>",
	"InitialProgram":"<initial program",
	"Title":"<title>",
	"Address":"<ip address>",
	"Username":"<user name>",
	"wsPort":"<port val>"
}
var launchData = {"type" : "json",value : icaObj};
sessionObject.start(launchData);
Example 2 : When ICA data is in INI format
var launchData = {"type" :"ini",value :"<ica data in ini format>"};
sessionObject.start(launchData);
```
Events

onConnection

To receive various states during the connection from client to server.
Type:

object
### Properties:

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>state</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Different connection states below : <br>"connecting" : Raised when connection starts before displaying connection dialog. <br>"connected" : Raised when connection is complete and when server and client starts exchanging data. <br>"sessionReady" : Raised when session is fully initialized, launched and ready for user interaction. <br></td></tr></tbody></table>
### Example

Sample event object generated for onConnection event.	
```				
{	
	"id":"<session id>",
	"type" : "onConnection",
	"data":{
		"state" : "connecting" // Event is triggered 3 times with different states mentioned above.
	}
}
```
onConnectionClosed

Raised when the connection with the server is closed.
### Example

Sample event object generated for onConnectionClosed event.				
```
{	
	"id":"<session id>",
	"type" : "onConnectionClosed",
}
```
onError

Raised on occurrence of any error in Citrix Receiver.
Type:

object
### Properties:

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>id</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">String ID defined in &lt;locale_file&gt;.js. For example, en.js would be for English, ko.js for Korean etc., ID remains the same for all locales supported.</td></tr><tr> <td class="name"><code>message</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Localized error message for the key. Customer can provide custom string in the language file to get meaningful error in the context of the deployment.</td></tr></tbody></table>
### Example

Sample event object generated for onError event.				
```
{	
	"id":"<session id>",
	"type" : "onError",
	"data":{
			"id":"<key_in_locale_file>" 
			"message" : "<value_for_the_key_in_locale_file>"
		}
}							
onToolbarBtnClick_btn_id
```
Raised when the custom toolbar button with id equal to btn_id is clicked.
### Example

Sample event object generated for onConnectionClosed event.				
```
{	
	"id":"<session id>",
	"type" : "onToolbarBtnClick_btn_id",
	"data" : {
			"id" : <btn_id>
	}
}
```
onURLRedirection

Raised when URL redirection is configured on server and when any URL is passed to the HTML5 engine to process. The message would contain the URL that is redirected to the client.
Type:

object
### Properties:

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>url</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">The value of the url would contain the URL that is redirected to the client.</td></tr></tbody></table>
### Example

Sample event object generated for onURLRedirection event.		
```								
{	
	"id":"<session id>",
	"type" : "onURLRedirection",
	"data":{
		"url" : "<url_received_to_redirect>"
	}
}
```
