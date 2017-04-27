# Travel Filter Component

### Component Use

```javascript

<t-filter data=[[data]] settings=[[settings]] resources=[[resources]]>
<template>
//this will be shown below the filter heading and above start of first filter option
<img src="" />
</template>
</t-filter>

```

### Filter Data
```javascript
[
	{
		"code": "hotel",
		"title": "Hotel Name",
		"type": "Text",
		"helpText": "Search by activity/hotel name",
		"isOpen": true,
		"selected": "",
		//If data is present it is used for providing autosuggest else no  
		"data": [
			"Howard Johnson",
			"Hilton Delux",
			"Holiday Inn"
		]
	},
	{
		"code": "price",
		"title": "Budget/Price",
		"type": "Option",
		"isOpen": false,
		//If there are more than default options then 'Show More' will be shown - which will show all and say 'Show Less'
		"defaultOptions": 5,
		"selected": [],
		//when multi select is allowd then checkboxes are shown 
		"allowMultiSelect": true,
		//this will show hover behaviour on desktop to apply only this option item by resetting all other filters		
	        "enableSelectionOveride":true,
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
				"isEnabled": false
			}
		],
		"allowSearch": true
	},
	{
		"code": "nearby",
		"title": "Nearby Area",
		"type": "Option",
		"isOpen": true,
		//If there are more than default options then 'Show More' will be shown - which will show all and say 'Show Less'
		"defaultOptions": 5,
		"selected": [],
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
		"title": "Rating",
		"type": "Rating",
		"code": "rating",
		"isOpen": false,
		//If there are more than default options then 'Show More' will be shown - which will show all and say 'Show Less'
		"defaultOptions": 5,
		"selected": [],
		//when multi select is not allowed then radio buttons should be shown 
		"allowMultiSelect": true,
		//this will show hover behaviour on desktop to apply only this option item by resetting all other filters		
	        "enableSelectionOveride":true,
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
		"title": "Distance",
		"type": "Range",
		"code": "dist",
		"isOpen": false,
		"selected": [
			4.5,
			7.5
		],
		"minValue": 1,
		"maxValue": 245,
		"step": 0.5,
		//When true it shows two markers
		"isSingleMarker": false
	},
	{
		"code": "curr",
		"title": "Currency",
		//This shows as a dropdown
		"type": "Select",
		"isOpen": true,
		"selected": "",
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
	},
	{
		"code": "dp",
		"title": "Distance with price",
		//Any number of known filter types (Text,Option,Rating,Range,Select) can be used inside a group  
		//The whole group can be expanded or collapses not individual sections 
		"type": "Group",
		"isOpen": false,
		"options": [
			{
				"title": "Price",
				"code":"dp-price",
				"type": "Range",
				"selected": [],
				"minValue": 100,
				"maxValue": 545,
				"step": 10,
				//When true it shows two markers
				"isSingleMarker": false
			},
			{
				"title": "Distance from city center",
				"code":"dp-dist",
				"type": "Range",
				"selected": [],
				"minValue": 0,
				"maxValue": 10,
				"step": 0.5,
				//When true it shows two markers
				"isSingleMarker": true
			}
		]
	},
	{
		"code": "pc",
		"title": "Price & category",
		//Any number of known filter types (Text,Option,Rating,Range,Select) can be used inside a group  
		//The whole group can be expanded or collapses not individual sections 
		"type": "Group",
		"isOpen": true,
		"options": [
			{
				"title": "Price",
				"code":"pc-price",
				"type": "Range",
				"selected": [],
				"minValue": 100,
				"maxValue": 545,
				"step": 10,
				//When true it shows two markers
				"isSingleMarker": false
			},
			{
				"title": "Hotel category",
				"type": "Select",
				"code":"pc-cat",
				"selected": "Deluxe",
				"allowMultiSelect": true,
				"data": [
					{
						"primary": "Premium",
						"secondary": "200"
					},
					{
						"primary": "Deluxe",
						"secondary": "100"
					},
					{
						"primary": "Budget",
						"secondary": "145"
					}
				]
			}
		]
	},
]
```


### Resources
```javascript
{
	"title": "Filter hotels by",
	"resetButtonText": "Reset",
	"applyButtonText": "Apply",
	"moreLinkText": "Show more",
	"lessLinkText": "Show less",
	"optionResetText":"reset"
}
```
### Settings
```javascript
{
	"collapsableHeader":true,
	"optionLevelReset":true,
	//when true it will show loading
	"showLoading":true
}
```

### Events
```javascript

Raises
t-filter-item-tap - {	"code": "price","selected": []}
t-filter-apply    - [{"code": "curr","selected": []},{"code": "price","selected": [{"primary": "$75 to $124"}]}]
t-filter-hotel-item-apply    { "code": "price","selected": []}
t-filter-{item code}-item-apply

Listens
t-filter-item-reset - {"code":"price", "index":2} (any one can be provided)
t-filter-reset
t-filter-update-state - (data as returned from getState())  -- will be fired for dependent filter data update

```

### Methods
```javascript

getState() - returns current filter state object

```

### Info
```javascript

- In mobile view Apply will be show and it will fire all applied filters data
- In case of no data the filter will show as collapsed or only the header will be visible
- In case of radio list if no selected value is given then no radio will be shown as selected

```

### Style
```javascript
- Need variable for defining header colour
- Need variable for defining border colour
- Loader mixin to set class or image details
- Need variable to control max filter height - it will show scroll when more data is there
```
## Important Information
- In mobile view- Filter event should be raised on click on APPLY button (not on individual selection)
- In desktop and Tablet, filter event will fire on every action (on every selection of filter option) and corrosponding results should change
- APPLY/RESET Link in mobile should be enabled only if atleast 1 filter is applied. (till than should appear as disabled)
- RESET link should clear all applied filters, behavior same across all devices.
- Title for every filter, can max occupy 1 line across all devices and trim for length names (show on toll tip)
- Title mentioned in resources, max can occupy 1 line across all devices and after that trim
- In filter data - Primary text should always be on left hand side and secondary on right hand. Secondary text should be in brackets.
- Hotel Name filter - If some text is selected or written in name field, on click it should get selected so that user can override it easily.
- Filters - "Show more" link should appear after mentioned value of "defaultOptions = 5" but if options in filter are less than 5, link should not appear.
- Filter data - Options name (primary text) can max occupy 2 lines and trim after that and full name on tool tip

## Test Cases
- Verify all exposed public properties are working independently and with complex combination.
- Verify all exposed methods and events are working.

## Steps to Start
- Set Github repository at your end for this project, we will merge them later
- You can use Google/Vaadin's elements (like calender element and textboxes etc.)
- You can use some Tavisca's elements like auto-suggest if required from https://github.com/atomelements/t-autosuggest but all the features and properties mentioned in scope should be added. (Fork the existing element and create V2)

## Performance standard
- Any component if opened via [web page tester](https://www.webpagetest.org/), it should load under 500ms (milli seconds).

## Documents
- Visual designs for filter component - https://projects.invisionapp.com/share/6E9PJ7R4Q#/screens/219768213
- Travel filter versions - https://projects.invisionapp.com/share/6E9PJ7R4Q#/screens/227194562
- API access : Url - http://demo.travelnxt.com/dev
- Tavisca Elements - https://github.com/atomelements and https://github.com/travelnxtelements
- Vaadin elements - https://vaadin.com/docs/-/part/elements/elements-getting-started.html
- Google - https://elements.polymer-project.org/browse?package=google-web-components
- Tavisca Web component style Guide - https://drive.google.com/open?id=0B7BT_2nBFNYVR2tscE9pRnVJYmc


