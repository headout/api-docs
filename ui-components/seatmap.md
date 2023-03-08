# Web components

## Seatmap Inventory
Since the inventory is seat-based in this situation, there is a unique inventory for each seat. Due to the possibility of various pricing and position for each seat, it is crucial to visualise the seatmap inventory.However, with just api support, drawing this layout can grow tiresome for our partners. Hence we offers it as ready-made web component for seatmap inventory and there is no api support. This web component can be loaded through Iframe within partners website.

All communication therefore happens through postMessage to Iframe and event listeners for receiving messages.

**Iframe Url** - /seatmap/tour-group/:productId

For this Iframe to work we need to set date, time, currencyCode, deviceType which is done by initPlugin explained below in events or you can you use directly use the Iframe by passing an additonal param showOnly=true along with these parameters

Ex - 
```
https://www.headout.com/seatmap/tour-group/3023?date=2023-03-11&time=19:30:00&deviceType=MOBILE&currencyCode=GBP&showOnly=true
```

P.S - Not all domains are allowed to use this Iframe to prevent misue. Please register your domain with us to use this Iframe

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

options = {
    'date' : '2023-03-03',
    'time' : '19:30:00',
    'currencyCode' : 'GBP',
	'deviceType' : 'MOBILE' | 'DESKTOP'
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

**removeSeat** - This event is triggered to add a seat within seatmap from any interaction outside Iframe. This expects an object with id element as data along with the event. Id is part of seat object.

**selectSeats** - This event removes the previous selected seats within Iframe and adds the new seats. This expects an object with bookableIds element as data along with the event


### Our seatmap Iframe will also send certain events to the parent window

To receive events from Iframe you can use event listener shown in the example below

```javascript
window.addEventListener('message', message => {
        const {data: stringifyData, origin} = message;
        const parsedData = JSON.parse(stringifyData);
        const {data, type} = parsedData;
        switch (type) {
            case 'onSeatAdded': {
                // do stuff
            }
        }
    }
);
```

As seen in the example above with each message contains origin and data
is stringified object of actual data and type

These are the types of events that you will receive from Iframe

**onSeatAdded** - Triggered when seat is selected within Iframe. With this event you will receive seat object being added as data. 

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

	
