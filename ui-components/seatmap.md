# Web components

## Seatmap Inventory
As Inventory is seat based here which means for each seat there is a unique inventory.There could be different prices and position for each of the seat which means proper visualizations becomes very important for selling these seats.However painting this layout can become very tedious for our partners with the api hence we offers it as readmade UI component for inventory and there is no api support. This UI component can be loaded through Iframe within partners website.

All communication therefore happens through postMessage to Iframe and event listeners for receiving messages.

To send events to Iframe you can use the following code snippet

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
Our Iframe listens to following types of events

**initPlugin** - This is to initalize the Iframe. On load of Iframe all consumers must send this message with the configuration options

Ex - 

```javascript
<iframe						
    onLoad={() => {
        sendMessageToIframe("initPlugin", options)
    }}
/>

options: {
    date,
    time
    currencyCode,
	deviceType
}
```

**setInventorySlot** - This is to trigger date/time change to load new Iframe.With this we expect the following data to be send
 {
    date,
    time
    currencyCode
}

selectSeats

**addSeat** - This event is triggered if for any usecase a seat should be added from selected seats within Iframe

**removeSeat** - This event is triggered if for any usecase a seat should be removed from selected seats within Iframe

Our seatmap Iframe will also send certain events to the parent window

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

**onSeatAdded** - Triggerd when seat is selected within Iframe. With this event you will receive seat object being added as data. 

**onSeatRemoved** - Triggered when seat is removed within Iframe. With this event you will receive seat object that is being removed.

**onSeatSelectionChanged** - Triggered when either seat is either added or removed.With this event you will recieve a current selection of seats as data

**inventoryUpdateStarted** - This is triggered when setInventorySlot method is called by consumner/parent window. This represents inventory update in progress corresponds to slot selected.

**inventoryUpdateCompleted** - This event is triggered after inventoryUpdateStarted when seatMap is loaded for particular slot(date/time combination)

**onZoomInButtonClick** - Triggered when zoom in button has been clicked within Iframe

**onZoomOutButtonClick** - Triggered when zoom out button has been clicked within Iframe

**onZoomResetButtonClick** - Triggered when reset button is clicked 

**onZoomLevelChanged** -Triggerd when zoom level has been changed for seatmap

**onPriceFilterClick** - Triggerd on click of price filters within Iframe.Consumers will also receive an array of priceFilters as data along with this event

**priceListOpened** - In Mobile devices Price Filter is hidden by default. This event is triggered when a price list is openend in mobile

**priceListClosed** - This event is triggered when a price list is closed

**clearFilterClicked** - This event is triggered when clearFilters is clicked in mobile view to remove price filters

**applyFilterClicked** - This event is triggered when apply filters is clicked in mobile view to apply price filters. 


Seat object
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
	
