---
layout: api-documentation
title : 'Spec: Make'
title_active_left_menu: 'Spec: Make'
title_parent: Api documentation

amount_version: 23
title-endpoint: 'Get A List of Makes'
spec: spec_make
version: v3
api: vehicle
dropdown-link: 'api/vehicle/v3/makes'


level: 3
description_edpoint: 'Get A List of Makes'
title_md : Description
number: 1
---

### Description

Get make details based on different filters.

### URL

    http://api.edmunds.com/api/vehicle/v3/makes?api_key={api key}&pageNum={pageNum}&pageSize={pageSize}&niceName={makeNiceName}
    
### Code Example

You need the [Javascript SDK](https://github.com/EdmundsAPI/edmunds-javascript-sdk) to run this example.

    <!DOCTYPE html>

    <html>
    <head>
        <meta charset=utf-8>
        <title>Get A List of Makes with Honda name</title>
    </head>

    <body>
        <div id="results-body"></div>
        <script>
              window.sdkAsyncInit = function() {
                // Instantiate the SDK
                var res = new EDMUNDSAPI('YOUR API KEY');

                // Optional parameters
                var options = {
                    "niceName": "honda",
                    "pagenum": 1,
                    "pagesize": 10
                };

                // Callback function to be called when the API response is returned
                function success(res) {
                    var body = document.getElementById('results-body');
                    body.innerHTML = "The make id with Honda name is " + 
                    res.results[0].id;
                }

                // Oops, Houston we have a problem!
                function fail(data) {
                    console.log(data);
                }

                // Fire the API call
                res.api('/api/vehicle/v3/makes', options, success, fail);

                // Additional initialization code such as adding Event Listeners goes here
          };

          // Load the SDK asynchronously
          (function(d, s, id){
                 var js, sdkjs = d.getElementsByTagName(s)[0];
                 if (d.getElementById(id)) {return;}
                 js = d.createElement(s); js.id = id;
                 js.src = "path/to/sdk/file";
                 sdkjs.parentNode.insertBefore(js, sdkjs);
           }(document, 'script', 'edmunds-jssdk'));
        </script>
    </body>
    </html>
