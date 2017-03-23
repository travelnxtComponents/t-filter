# Travel Filter Component

### Component Data

```javascript

[
	{
		"id": 1,
		"title": "Hotel Name",
		"type": "Text",
		"helpText": "Search by activity/hotel name",
		"isOpen": true,
		"selectedValues": "",
		//If data is present it is used for providing autosuggest else no  
		"data": [
			"Howard Johnson",
			"Hilton Delux",
			"Holiday Inn"
		]
	},
	{
		"id": 2,
		"title": "Budget/Price",
		"type": "Option",
		"isOpen": false,
		//If there are more than default options then 'Show More' will be shown - which will show all and say 'Show Less'
		"defaultOptions": 5,
		"selectedValues": [],
		//when multi select is allowd then checkboxes are shown 
		"allowMultiSelect": true,
		"data": [
			{
				"primary": "Less than $75",
				"secondary": "150"
			},
			{
				"primary": "$75 to $124",
				"secondary": "85"
			},
			{
				"primary": "$125 to $199",
				"secondary": "250",
				//this will show as disabled where user will not be abel to click it
				"isEnabled":false
			}
		],
		"allowSearch": true
	},
	{
		"id": 3,
		"title": "Nearby Area",
		"type": "Option",
		"isOpen": true,
		//If there are more than default options then 'Show More' will be shown - which will show all and say 'Show Less'
		"defaultOptions": 5,
		"selectedValues": [],
		//when multi select is not allowed then radio buttons should be shown 
		"allowMultiSelect": false,
		"data": [
			{
				"primary": "Main strip",
				"secondary": "150"
			},
			{
				"primary": "Green park",
				"secondary": "85"
			},
			{
				"primary": "Walking street",
				"secondary": "250"
			}
		],
		"allowSearch": true
	},
	{
		"id": 4,
		"title": "Rating",
		"type": "Rating",
		"isOpen": false,
		//If there are more than default options then 'Show More' will be shown - which will show all and say 'Show Less'
		"defaultOptions": 5,
		"selectedValues": [],
		//when multi select is not allowed then radio buttons should be shown 
		"allowMultiSelect": true,
		"data": [
			{
				"primary": 5,
				"secondary": "150"
			},
			{
				"primary": 4,
				"secondary": "85"
			},
			{
				"primary": 3.5,
				"secondary": "250"
			},
			{
				"primary": 3,
				"secondary": "270"
			},
			{
				"primary": 0,
				"secondary": "10"
			}
		],
		"allowSearch": false
	},
	{
		"id": 5,
		"title": "Distance",
		"type": "Range",
		"isOpen": false,
		"selectedValues": [
			4.5,
			7.5
		],
		"minValue": 1,
		"maxValue": 245,
		"step": 0.5,
		//When true it shows two markers
		"isSingleMarkers": false
	},
	{
		"id": 6,
		"title": "Distance with price",
		"type": "MultiRange",
		"isOpen": false,
		"options": [
			{
				"title": "Price",
				"selectedValues": [],
				"minValue": 100,
				"maxValue": 545,
				"step": 10,
				//When true it shows two markers
				"isSingleMarkers": false
			},
			{
				"title": "Distance from city center",
				"selectedValues": [],
				"minValue": 0,
				"maxValue": 10,
				"step": 0.5,
				//When true it shows two markers
				"isSingleMarkers": true
			}
		]
	},
	{
		"id": 7,
		"label": "Currency",
		"type": "Select",
		"isOpen": true,
		"selectedValues": "",
		"data": [
			{
				"primary": "United States",
				"secondary": "USD"
			},
			{
				"primary": "India",
				"secondary": "INR"
			},
			{
				"primary": "Canada",
				"secondary": "CAD"
			}
		]
	}
]
```
### Resources
```javascript
{
	"title": "Filter hotels by",
	"resetButtonText": "Reset",
	"applyButtontext": "Apply",
	"moreLinkText":"Show more",
	"lessLinkText":"Show less"
}
```
### Events
```javascript

t-filter-tap  data -{	"id": 1, "selectedValues": [] }
t-filter-apply data - [{"id": 1, "selectedValues": []},{"id": 2, "selectedValues": [{"primary": "$75 to $124"}]}]
t-filter-item-reset - {}
t-filter-reset
t-filter-update-state - (data as returned from getState())  -- will be fired for dependent filter data update

```
### Methods
```javascript

getState() - returns current filter state object

```
### Info
```javascript

In mobile view Apply will be show and it will fire all applied filters data

```
