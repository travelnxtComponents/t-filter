# Travel Filter Component

### Component Use

```javascript

<t-filter
        data ="{{data}}"
        resources ="{{resources}}"
</t-filter>

```

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
		//When true it shows two markers at both ends
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
t-filter-item-reset - [{"id": 1}]
t-filter-reset - {}
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
- 

## Steps to Start
- Set Github repository at your end for this project, we will merge them later
- You can use Google/Vaadin's elements (like calender element and textboxes etc.)
- You can use some Tavisca's elements like auto-suggest if required from https://github.com/atomelements/t-autosuggest but all the features and properties mentioned in scope should be added. (Fork the existing element and create V2)

## Performance standard
- Any component if opened via [web page tester](https://www.webpagetest.org/), it should load under 500ms (milli seconds).

## Documents
- Visual designs for filter component - https://projects.invisionapp.com/share/6E9PJ7R4Q#/screens/219768213
- API access : Url - http://demo.travelnxt.com/dev
- Tavisca Elements - https://github.com/atomelements and https://github.com/travelnxtelements
- Vaadin elements - https://vaadin.com/docs/-/part/elements/elements-getting-started.html
- Google - https://elements.polymer-project.org/browse?package=google-web-components
- Tavisca Web component style Guide - https://drive.google.com/open?id=0B7BT_2nBFNYVR2tscE9pRnVJYmc


