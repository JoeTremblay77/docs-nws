# PHP Samples

## PHP-cURL

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://servername/api/dealers',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'x-api-key: thisIsASampleKey'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

```

## PHP Guzzle

```php
<?php
$client = new Client();
$headers = [
  'x-api-key' => 'thisIsASampleKey'
];
$request = new Request('GET', 'https://servername/api/dealers', $headers);
$res = $client->sendAsync($request)->wait();
echo $res->getBody();
```

## PHP HTTP_REQUEST2

```php
<?php
require_once 'HTTP/Request2.php';
$request = new HTTP_Request2();
$request->setUrl('https://servername/api/dealers');
$request->setMethod(HTTP_Request2::METHOD_GET);
$request->setConfig(array(
  'follow_redirects' => TRUE
));
$request->setHeader(array(
  'x-api-key' => 'thisIsASampleKey'
));
try {
  $response = $request->send();
  if ($response->getStatus() == 200) {
    echo $response->getBody();
  }
  else {
    echo 'Unexpected HTTP status: ' . $response->getStatus() . ' ' .
    $response->getReasonPhrase();
  }
}
catch(HTTP_Request2_Exception $e) {
  echo 'Error: ' . $e->getMessage();
}
```

## PHP pecl_http

```php
<?php
$client = new http\Client;
$request = new http\Client\Request;
$request->setRequestUrl('https://servername/api/dealers');
$request->setRequestMethod('GET');
$request->setOptions(array());
$request->setHeaders(array(
  'x-api-key' => 'thisIsASampleKey'
));
$client->enqueue($request)->send();
$response = $client->getResponse();
echo $response->getBody();
```