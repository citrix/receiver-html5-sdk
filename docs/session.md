#Class: Session

##Session

#### <span class="type-signature"></span>new Session<span class="signature">()</span><span class="type-signature"></span>

### Members

#### <span class="type-signature"></span>container<span class="type-signature"></span>

Contains the type and value of the container where the session is launched.

##### Properties:

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>container</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="description last"> <h6>Properties</h6><table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>type</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Type of the container. Will be set to "iframe" or "window" when launchType is set to "embed" or "newtab" respectively.</td></tr><tr> <td class="name"><code>value</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="description last">Contains the iframe DOM object or reference to the window where the session is launched based on the launchType.</td></tr></tbody></table> </td></tr></tbody></table>
<br>
#### <span class="type-signature">(readonly) </span>id<span class="type-signature"></span>

##### Properties: {#properties-2 .subsection-title}

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>id</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">ID of the object.</td></tr></tbody></table>

### Methods 

#### <span class="type-signature">(inner) </span>addListener<span class="signature">(eventType, eventListener)</span><span class="type-signature"></span> 

Registers the eventListener on the eventType.

##### Parameters:

<table class="params"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>eventType</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Type of the event for which the listener needs to be attached.<br><br>Supported event types : <br><a href="/Session#~event:onConnection">onConnection</a><br><a href="/Session#~event:onConnectionClosed">onConnectionClosed</a><br><a href="/Session#~event:onURLRedirection">onURLRedirection</a><br><a href="/Session#~event:onError">onError</a><br></td></tr><tr> <td class="name"><code>eventListener</code></td><td class="type"> <span class="param-type"><a href="/global#eventListener">eventListener</a></span> </td><td class="description last">Listener to handle the event.</td></tr></tbody></table>

##### Example

```java
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

#### <span class="type-signature">(inner) </span>changeResolution<span class="signature">(bounds)</span><span class="type-signature"></span>

Changes the resolution of the session.

##### Parameters:

<table class="params"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>bounds</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="description last">Contain session resolution settings.</td></tr></tbody></table>

##### Properties:

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>bounds.autoresize</code></td><td class="type"> <span class="param-type">boolean</span> </td><td class="description last">Should be set to false to give fixed width and height to session. If this value is set to true then the session is resized to match the size of iframe element or the tab.</td></tr><tr> <td class="name"><code>bounds.width</code></td><td class="type"> <span class="param-type">Number</span> </td><td class="description last">Width of the session specified in pixels. This value will be set only when autoresize is set to false.</td></tr><tr> <td class="name"><code>bounds.height</code></td><td class="type"> <span class="param-type">Number</span> </td><td class="description last">Height of the session specified in pixels. This value will be set only when autoresize is set to false.</td></tr></tbody></table>

##### Examples

```java
Example 1 : To change resolution to fixed width and height  
var bounds = {
    "autoresize":false,
    "width": "800",
    "height":"600"
}
sessionObject.changeResolution(bounds);
```


``` java
Example 2 : To change the session resolution to match the iframe element or tab size   
var bounds = {
    "autoresize": true
}
sessionObject.changeResolution(bounds);
```

#### <span class="type-signature">(inner) </span>disconnect<span class="signature">()</span><span class="type-signature"></span> 

Disconnects the session.

#### <span class="type-signature">(inner) </span>removeListener<span class="signature">(eventType, eventListener)</span><span class="type-signature"></span>

Removes the eventListener on the eventType.

##### Parameters:

<table class="params"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>eventType</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Type of the event for which the listener needs to be removed.<br><br>Supported event types : <br><a href="/Session#~event:onConnection">onConnection</a><br><a href="/Session#~event:onConnectionClosed">onConnectionClosed</a><br><a href="/Session#~event:onURLRedirection">onURLRedirection</a><br><a href="/Session#~event:onError">onError</a><br></td></tr><tr> <td class="name"><code>eventListener</code></td><td class="type"> <span class="param-type"><a href="/global#eventListener">eventListener</a></span> </td><td class="description last">Listener to handle the event.</td></tr></tbody></table>

##### Example

``` java
//Removing the event handler for onConnection event
function connectionHandler(eventObj){
    console.log("Event Received : " + event.type);      
    console.log(event.data);
}
sessionObject.removeListener("onConnection",connectionHandler);
```

#### <span class="type-signature">(inner) </span>sendSpecialKeys<span class="signature">(keys)</span><span class="type-signature"></span> {#~sendSpecialKeys .name}

Sends a key combination to the session. In this version only
"ctrl+alt+del" is supported.

##### Parameters:

<table class="params"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>keys</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Key combination string.</td></tr></tbody></table>

##### Example

``` {.prettyprint}
var keys = "ctrl+alt+del"; //Only this key combination is supported in this version.
sessionObject.sendSpecialKeys(keys);
```

#### <span class="type-signature">(inner) </span>start<span class="signature">(launchData)</span><span class="type-signature"></span>

Starts the session.

##### Parameters:

<table class="params"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>launchData</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="description last">Contains the type and value of ICA.</td></tr></tbody></table>

##### Properties: 

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>launchData.type</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Specifies the data type of ICA data. Allowed values are "json" or "ini".</td></tr><tr> <td class="name"><code>launchData.value</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">ICA data to start the session. It should be a JSON object when type is "json" or a string read from a .ini file when type is "ini".</td></tr></tbody></table>

##### Examples

``` java
Example 1 : When ICA data is in JSON format                                
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
```
<br>
``` java
Example 2 : When ICA data is in INI format
var launchData = {"type" :"ini",value :"<ica data in ini format>"};
sessionObject.start(launchData);
```

### Events 

#### onConnection 

To receive various states during the connection from client to server.

##### Type:

>-   <span class="param-type">object</span>

##### Properties: {#properties-5 .subsection-title}

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>state</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Different connection states below : <br>"connecting" : Raised when connection starts before displaying connection dialog. <br>"connected" : Raised when connection is complete and when server and client starts exchanging data. <br>"sessionReady" : Raised when session is fully initialized, launched and ready for user interaction. <br></td></tr></tbody></table>

##### Example

``` java
Sample event object generated for onConnection event.    
                
{   
    "id":"<session id>",
    "type" : "onConnection",
    "data":{
        "state" : "connecting" // Event is triggered 3 times with different states mentioned above.
    }
}
```

#### onConnectionClosed

Raised when the connection with the server is closed.

##### Example

``` json
Sample event object generated for onConnectionClosed event.              

{   
    "id":"<session id>",
    "type" : "onConnectionClosed",
}
```

#### onError

Raised on occurrence of any error in Citrix Receiver.


##### Type:

>-   <span class="param-type">object</span>

##### Properties:

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>id</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">String ID defined in &lt;locale_file&gt;.js. For example, en.js would be for English, ko.js for Korean etc., ID remains the same for all locales supported.</td></tr><tr> <td class="name"><code>message</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Localized error message for the key. Customer can provide custom string in the language file to get meaningful error in the context of the deployment.</td></tr></tbody></table>

##### Example

``` json
Sample event object generated for onError event.             

{   
    "id":"<session id>",
    "type" : "onError",
    "data":{
            "id":"<key_in_locale_file>" 
            "message" : "<value_for_the_key_in_locale_file>"
        }
}                           
```

#### onURLRedirection {#~event:onURLRedirection .name}

Raised when URL redirection is configured on server and when any URL is passed to the HTML5 engine to process. The message would contain the URL that is redirected to the client.

##### Type:

>-   <span class="param-type">object</span>

##### Properties: 

<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>url</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">The value of the url would contain the URL that is redirected to the client.</td></tr></tbody></table>

##### Example

``` json
Sample event object generated for onURLRedirection event.        
                                
{   
    "id":"<session id>",
    "type" : "onURLRedirection",
    "data":{
        "url" : "<url_received_to_redirect>"
    }
}               
```
