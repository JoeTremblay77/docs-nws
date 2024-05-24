# API Helper for NS

A an API made available to applications that provide a valid API key and are permitted access through a firewall.  This application does not update data and only returns basic inventofy and pricing data. No personal identifiers are exposed.


## Configuration

### API Key

All requests must supply an API key. This key is a string value contained in the root app.config file.  The key, can actually be any value, but for best practice it should a GUID or similar type of string.  At any time, the key can be updated; however, you will need to ensure that all calling applications have been provided the new key. 


* Every request must supply an HTTP Header:   x-api-key
* For example, if the API key in the app.config was "abc123" then the request to the test endpoint would be: 

```cURL
curl --location 'http://localhost:5002/dealerlookupapp/api/test' --header 'x-api-key: abc123'
```

### API Endpoints Available

**GET /api/dealers**: Retrieves the dealers in a standard api response below. 

**GET /api/dealers/forcefail**: A developer utility to create a fake failure response for testing. 

**GET api/test**: A test endpoint for development to check that the x-api-key was supplied and is correct. 


### Samples

- [PHP Samples](PHPSamples.md)





