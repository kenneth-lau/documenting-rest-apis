# Resource description

<!--The Surf Report API lets you check tide and wave conditions and also provides a recommendation for whether to go hit the waves or not.-->

## surfreport/{beachId}
Returns information about surfing conditions at a specific beach ID, including the surf height, water temperature, wind, and tide. Also provides an overall recommendation about whether to go surfing.

`{beachId}` refers to the ID for the beach you want to look up. All Beach ID codes are available from our site.

# Endpoint
`get` `surfreport/{beachID}`

# Methods


# Parameters
|Parameter|Required|Description|Type|
|---|---|---|---|
|days|Optional|Number of days to include. Default: 3|Integer|
|units|Optional|Either `imperial` or `metric`|string|
|time|Optional|If you include the time, only the current hour wil be returned|integer (Unix format)|

# Request submission example

```
curl --get --include 'https://simple-weather.p.mashap .com/surfreport/123?units=imperial&days=1&time=1433772000' -H 'X-Mashape-Key: APIKEY' -H 'Accept: application/json'
```

# Request response example

```
{
    "surfreport": [
        {
            "beach": "Santa Cruz",
            "monday": {
                "1pm": {
                    "tide": 5,
                    "wind": 15,
                    "watertemp": 80,
                    "surfheight": 5,
                    "recommendation": "Go surfing!"
                },
                "2pm": {
                    "tide": -1,
                    "wind": 1,
                    "watertemp": 50,
                    "surfheight": 3,
                    "recommendation": "Surfing conditions are okay, not great."
                },
                "3pm": {
                    "tide": -1,
                    "wind": 10,
                    "watertemp": 65,
                    "surfheight": 1,
                    "recommendation": "Not a good day for surfing."
                }
            }
        }
    ]
}
```
|Response item|Description|
|---|---|
|beach|The beach you selected based on the beach ID in the request. The beach name is the official name as described in the National Park Service Geodatabase.|
|{day}|The day of the week selected. A maximum of 3 days get returned in the response.|
|{time}|The time for the conditions. This item is only included if you include a time parameter in the request.|
|{day}/{time}/tide|The level of tide at the beach for a specific day and time. Tide is the distance inland that the water rises to, and can be a positive or negative number. When the tide is out, the number is negative. When the tide is in, the number is positive. The 0 point reflects the line when the tide is neither going in nor out but is in transition between the two states.|

# Status and error codes

# Code samples
The following code samples shows how to use the surfreport endpoint to get the surf conditions for a specific beach. In this case, the code shows the overall recommendation about whether to go surfing.

```html
<!DOCTYPE html>
<head>
<script src="http://code.jquery.com/jquery-2.1.1.min.js"></script>
<script>
var settings = {
  "async": true,
  "crossDomain": true,
  "dataType": "json",
  "url": "https://simple-weather.p.mashape.com/surfreport/25",
  "method": "GET",
  "headers": {
    "accept": "application/json",
    "x-mashape-key": "APIKEY"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
  $("#surfheight").append(response.query.results.channel.surf.height);
});
</script>
</head>
<body>
<h2>Surf Height</h2>
<div id="surfheight"></div>
</body>
</html>
```

In this example, the `ajax` method from jQuery is used because it allows us to load a remote resource asynchronously.

In the request, you submit the authorization through the header rather than directly in the endpoint path. The endpoint limits the days returned to 1 in order to increase the download speed.

For demonstration purposes, the `response` is assigned to the response argument of the `done` method, and then written out to the `surfheight` tag on the page.

We're just getting the surf height, but there's a lot of other data you could choose to display.
