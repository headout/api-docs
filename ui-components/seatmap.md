# Web components

## Seatmap Inventory
Given that the inventory in this scenario is based on seats, it implies that there is distinct inventory for each seat. Visualizing the seatmap inventory becomes essential due to the variations in pricing and positioning for each individual seat.However, with just api support, drawing this layout can grow tiresome for our partners, hence we offer it as ready-made web component to display seatmap inventory and there is no api support. This web component can be loaded through Iframe within partners website.

All communication through Iframe therefore happens through postMessage for sending messages and event listeners for receiving messages.Here is the url structure for Iframe

**Iframe Url** - https://www.headout.com/seatmap/tour-group/:productId

For this Iframe to work we need to set date, time, currencyCode, deviceType which is done by initPlugin event explained below in events or you can you also directly use the Iframe by passing an additonal param showOnly=true along with parameters of initPlugin event

Ex - 
```
https://www.headout.com/seatmap/tour-group/3023?date=2023-03-11&time=19:30:00&deviceType=MOBILE&currencyCode=GBP&showOnly=true
```

P.S - Not all domains are allowed to use this Iframe to prevent misuse. Iframe access will be blocked under the browser CSP policies.You have to register your domain with us to use this Iframe. To register talk to business team you are in touch or drop and emal to tech@headout.com

### Events can be sent to Iframe using postMessage. Ex -

```javascript
sendMessageToIframe = (type, data) => {
	const iframeWindow = IframeRef.contentWindow;
	if (iframeWindow) {
		iframeWindow.postMessage(
			JSON.stringify({
				type,
				data,
			}),
			'*',
		);
	}
};
```
### Our Iframe listens to following types of events

**initPlugin** - This is to initalize the Iframe. Initalization can be done either through passing relevant config options in Iframe url or by triggering this event.All consumers must send some config options as explained in example below


```javascript
<iframe						
    onLoad={() => {
        sendMessageToIframe("initPlugin", options)
    }}
/>

options: {
    date: '2023-03-03',
    time: '19:30:00'
    currencyCode: 'GBP',
	deviceType: 'MOBILE' | 'DESKTOP'
}
```

**setInventorySlot** - This is to trigger date/time change to load new inventory in Iframe for this slot.With this we expect the following data to be send
 {
    date,
    time
    currencyCode
}



**addSeat** - This event is triggered to add a seat within seatmap from any interaction outside Iframe. This expects an object with id element as data along with the event. Id is part of seat object.

Ex - 
```javascript
sendMessageToIframe("addSeat", { id })
```

This is the contract of Seat Object
```javascript
Object: Seat
{
	id
	currency
	seatNumber,
	seatRow: row.attr("display"),
	color: seat.attr("allotedSeatColor"),
	seatCode: seat.attr("display").concat(row.attr("display")),
	seatSection: section.attr("display"),
	remaining: parseInt(seat.attr("remaining")),
	maxAvailable: parseInt(seat.attr("max-available")),
	description: seat.attr("description"),
	price,
	originalPrice,
	discounted: originalPrice > price,
}
```

If you are wondering how do you get these values. Most of these values are part of html itself in Iframe. If you have to fetch it you have to fetch it from html attributes of seat node.

**removeSeat** - This event is triggered to remove a seat within seatmap from any interaction outside Iframe. This expects an object with id element as data along with the event. Id is part of seat object.

**selectSeats** - This event removes the previous selected seats within Iframe and adds the new seats. This expects an object with bookableIds element as data along with the event


### Our seatmap Iframe will also send certain events to the parent window

To receive events from Iframe you can use event listener shown in the example below

```javascript
window.addEventListener('message', message =>
	const { data: stringifyData, origin } = message;
	const parsedData = JSON.parse(stringifyData);
	const { data, type } = parsedData;
	switch (type) {
		case 'onSeatAdded': {
			// do stuff
		}
);
```

As seen in the example above with each message contains origin and data
data is stringified object of actual data and type

These are the types of events that you will receive from Iframe

**onSeatAdded** - Triggerd when seat is selected in Iframe. With this event you will receive seat object being added as data. 


**onSeatRemoved** - Triggered when seat is removed in Iframe. With this event you will receive seat object that is being removed.

**onSeatSelectionChanged** - Triggered when either seat is added or removed.With this event you will recieve a current selection of seats as data

**inventoryUpdateStarted** - This is triggered when setInventorySlot method is called by consumner/parent window. This represents inventory update in progress corresponds to slot selected.

**inventoryUpdateCompleted** - This event is triggered after inventoryUpdateStarted when seatMap is loaded for particular slot(date/time combination)

**onZoomInButtonClick** - Triggered when zoom in button has been clicked within Iframe

**onZoomOutButtonClick** - Triggered when zoom out button has been clicked within Iframe

**onZoomResetButtonClick** - Triggered when reset button is clicked 

**onZoomLevelChanged** -Triggerd when zoom level has been changed for seatmap

**onPriceFilterClick** - Triggerd on click of price filters within Iframe.Consumers will also receive an array of selected priceFilters as data along with this event

**priceListOpened** - In Mobile devices Price Filter is hidden by default. This event is triggered when a price list is openend in mobile

**priceListClosed** - This event is triggered when a price list is closed

**clearFilterClicked** - This event is triggered when clearFilters is clicked in mobile view to remove price filters

**applyFilterClicked** - This event is triggered when apply filters is clicked in mobile view to apply price filters. 

	
