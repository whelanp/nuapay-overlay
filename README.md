# nuapay-overlay
Demo how to overlay emandates in your application

This javascript code shows how to overlay the emandate application in your own application.

## Steps
1.  Server Side make a call to [prepateMandate](https://docs.nuapay.com/v1/#prepare-e-mandate) this setups up the merchant information for the emandate, you can optionally prefill the debtor details if you know them, it's important also to set the property [domain](https://docs.nuapay.com/v1/#e-mandate-object) of the merchant details. This enables the emandate to be displayed in an overlay on your domain only.
1. Include the nuapay.js file in your website.
1. To display the overlay call the method displayOverlay with the parameter of token returned in step 1.
1. To hide the overlay call the method removeOverlay.
1. You can listen out for success and failure of the mandate signing process by adding a window EventListener. See sample code below.
1. Contact support@nuapay.com if you have any further questions.

```javascript
//simply show the emandate overlay with displayOverlay(token);
//simply hide the emandate overlay with removeOverlay();

//sample event listener to listen out for success/failure event of mandate siging process
window.addEventListener("message", receiveMessage, false);
function receiveMessage(event)
{
	var json = JSON.parse(event.data);	
	//deal with the json message if you choose to do so.
	if(json.status===1) {
		console.log("Success");
	}
	else {
		console.log("failure");
	}
	//either way remove the overlay when the flow is completed
	removeOverlay();
}```