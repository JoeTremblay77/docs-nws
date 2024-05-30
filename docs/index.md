# Dealer API

The "Dealer API" enables a publically available hosted website to retrieve the list of Dealers from an on-premise repository.  It is a RESTful JSON API which implies:

* There is no state management that takes place in API. Every call is an isolated, distinct request.
* All results from authenticated calls are returned in a JSON format.  Keep in mind that invalid API Keys do not provide a JSON response. 

## Security Considerations

The API was purpose built to provide secure access to internal data from an outside application.  To accomplish this, the following was incorporated: 

1. Every API call requires an API Key to be provided. It is enforced using the very latest Web API framework. 
2. The API is accesses only through an HTTPS connection which ensures that the API Key and data exchanged are encrypted.
3. Although the API provides robust application level security, it is expected that IP whitelisting and DDOS prevention are configured within the firewall.  When consuming the API, if you receive a 404 Not Found it is most likely because of a whitelisting restriction. 

## Usage

### API Key

All requests must supply an API key. Upon request, or if suspicious activity is detected, the key can be quickly updated using the API configuration file. 

* Every request must supply an HTTP Header:   x-api-key
* For example, if the API key was "abc123" then the request to the test endpoint would be: 

```cURL
curl --location 'http://{TheWebsiteURLHere}/dealerlookupapp/api/test' --header 'x-api-key: abc123'
```

### API Endpoints Available

**GET /api/dealers**: Retrieves **all** of the dealers in a standard api response below. 

**GET /api/dealers??item=&brand=&showUnitsOnly=true**: Retrieves a **filtered** list of the dealers in a standard api response below. Item and Brand use a 'Contains' style search.  If showUnitsOnly is not supplied, it will be defaulted to 'false'.

**GET /api/dealers/forcefail**: A developer utility to create a fake failure response for testing. 

**GET api/test**: A test endpoint for development to check that the x-api-key was supplied and is correct. 


### Samples

- [PHP Samples](PHPSamples.md)





