
<h1 id="ClickSend-v3-API-SMS">SMS</h1>

## <span class="request post"></span>Send SMS

> Code samples

```shell
curl --include \
     --request POST \
     --header "Content-Type: application/json" \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
     --data-binary "    {
        \"messages\":[
            {
                \"source\":\"php\",
                \"from\":\"sendmobile\",
                \"body\":\"Jelly liquorice marshmallow candy carrot cake 4Eyffjs1vL.\",
                \"to\":\"+61411111111\",
                \"schedule\":1436874701,
                \"custom_string\":\"this is a test\"
            },
            {
                \"source\":\"php\",
                \"from\":\"sendlist\",
                \"body\":\"Chocolate bar icing icing oat cake carrot cake jelly cotton MWEvciEPIr.\",
                \"list_id\":428,
                \"schedule\":1436876011,
                \"custom_string\":\"this is a test\"
            }
        ]
    }" \
'https://rest.clicksend.com/v3/sms/send'
```

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

// Configure HTTP basic authorization: BasicAuth
$config = Swagger\Client\Configuration::getDefaultConfiguration()
    ->setUsername('USERNAME')
    ->setPassword('API_KEY');

$apiInstance = new Swagger\Client\Api\SMSApi(
    new GuzzleHttp\Client(),
    $config
);

$msg = new \Swagger\Client\Model\SmsMessage();

$msg->setFrom("Test"); // Optional - Business name up to 11 characters, personal mobile number, or ClickSend dedicated number
$msg->setBody("test body"); // Required
$msg->setTo("0451111111"); // Optional - Requires either setTo or setListId ($msg->setListId(1))
$msg->setSource("php-sdk");

$sms_messages = new \Swagger\Client\Model\SmsMessageCollection();

$sms_messages->setMessages([$msg]);

try {
    $result = $apiInstance->smsSendPost($sms_messages);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SMSApi->smsSendPost: ', $e->getMessage(), PHP_EOL;
}
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "messages": [
    {
      "schedule": 0,
      "country": "country",
      "from_email": "from_email",
      "list_id": 0,
      "from": "from",
      "to": "69505609",
      "source": "sdk",
      "body": "body",
      "custom_string": "custom_string"
    },
    {
      "schedule": 0,
      "country": "country",
      "from_email": "from_email",
      "list_id": 0,
      "from": "from",
      "to": "69505609",
      "source": "sdk",
      "body": "body",
      "custom_string": "custom_string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://rest.clicksend.com/v3/sms/send',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://rest.clicksend.com/v3/sms/send',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
from __future__ import print_function
import time
import clicksend_client
from clicksend_client import SmsMessage
from clicksend_client.rest import ApiException
from pprint import pprint

# Configure HTTP basic authorization: BasicAuth
configuration = clicksend_client.Configuration()
configuration.username = 'USERNAME'
configuration.password = 'API_KEY'

# create an instance of the API class
api_instance = clicksend_client.SMSApi(clicksend_client.ApiClient(configuration))
sms_message = SmsMessage(source='php', _from='sendmobile', body='Jelly liquorice marshmallow candy carrot cake 4Eyffjs1vL.', to='+61411111111', schedule=1436874701, custom_string='this is a test')
sms_messages = clicksend_client.SmsMessageCollection(messages=[sms_message])

try:
    # Send sms message(s)
    api_response = api_instance.sms_send_post(sms_messages)
    pprint(api_response)
except ApiException as e:
    print('Exception when calling SMSApi->sms_send_post: %s\n' % e)

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/send");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://rest.clicksend.com/v3/sms/send", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Body parameter

```json
{
  "messages": [
    {
      "schedule": 0,
      "country": "country",
      "from_email": "from_email",
      "list_id": 0,
      "from": "from",
      "to": "69505609",
      "source": "sdk",
      "body": "body",
      "custom_string": "custom_string"
    },
    {
      "schedule": 0,
      "country": "country",
      "from_email": "from_email",
      "list_id": 0,
      "from": "from",
      "to": "69505609",
      "source": "sdk",
      "body": "body",
      "custom_string": "custom_string"
    }
  ]
}
```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Here are your data.",
  "data": {
    "total_price": 0.28,
    "total_count": 2,
    "queued_count": 2,
    "messages": [
      {
        "direction": "out",
        "date": 1436871253,
        "to": "+61411111111",
        "body": "Jelly liquorice marshmallow candy carrot cake 4Eyffjs1vL.",
        "from": "sendmobile",
        "schedule": 1436874701,
        "message_id": "BF7AD270-0DE2-418B-B606-71D527D9C1AE",
        "message_parts": 1,
        "message_price": 0.07,
        "custom_string": "this is a test",
        "user_id": 1,
        "subaccount_id": 1,
        "country": "AU",
        "carrier": "Telstra",
        "status": "SUCCESS"
      },
      {
        "direction": "out",
        "date": 1436871253,
        "to": "+61411111111",
        "body": "Chocolate bar icing icing oat cake carrot cake jelly cotton MWEvciEPIr.",
        "from": "sendlist",
        "schedule": 1436876011,
        "message_id": "D0C273EE-816D-4DF2-8E9D-9D9C65F168F3",
        "message_parts": 1,
        "message_price": 0.07,
        "custom_string": "this is a test",
        "user_id": 1,
        "subaccount_id": 1,
        "country": "AU",
        "carrier": "Telstra",
        "status": "SUCCESS"
      }
    ],
    "currency": {
      "currency_name_short": "USD",
      "currency_prefix_d": "$",
      "currency_prefix_c": "¢",
      "currency_name_long": "US Dollars"
    }
  }
```

<span class="method post"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/send</span>

*Send sms message(s)*

### How many messages can I send?

You can post `up to 1000 messages` with each API call. You can send to a mix of contacts and contact lists, as long as the total number of recipients is up to 1000. The response contains a status and details for each recipient.

Refer to [**Application Status Codes**](#application-status-codes) for the possible response message status strings.

### *SMS Campaign Endpoint*

You can post to a list with `up to 20000 recipients` with each API call. You can only send to a single list containing up to 20,000 recipients. The response is far less detailed than the normal Send SMS endpoint.

### How many characters can I send in a message?

A standard SMS message has a maximum of 160 characters. Longer messages are definitely possible, however please be aware that exceeding 160 characters will constitute a ‘second’ message. The end user will see this as 1 long message on their handset.
When a message is longer than 160 characters, this is referred to as a multi-part message as it contains multiple messages (or multiple-parts). The total SMS limit then becomes 153 characters per ‘part’ as the 7 characters are used up by invisible headers and footers which denote which part of the message is being sent (i.e. Part 1 of 2). For example:
If a message is longer than 6 message parts, it will be truncated (see below). If a message contains any characters that aren't in the GSM 03.38 character set, the message type will be treated as unicode. 
(<a href="https://en.wikipedia.org/wiki/GSM_03.38" rel="noopener" target="_blank">https://en.wikipedia.org/wiki/GSM_03.38</a>)

### *Standard English Characters:*

| Number of Characters | Message Credits |
|---|---|
| 1 - 160 | 1 |
| 161 - 306 | 2 |
| 307 - 459 | 3 |
| 460 - 612 | 4 |
| 613 - 765 | 5 |
| 766 - 918 | 6 |
| 919 - 1071 | 7 |
| 1072 - 1224 | 8 |

### *Non-GSM (Unicode) characters:*

| Number of Characters | Message Credits |
|---|---|
|1 - 70 | 1 |
|71 - 134 | 2 |
|135 - 201 | 3 |
|202 - 268 | 4 |
|269 - 335 | 5 |
|336 - 402 | 6 |
|403 - 469 | 7 |
|470 - 536 | 8 |

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|from|string|true|[yes](http://help.clicksend.com/SMS/what-is-a-sender-id-or-sender-number)|Your sender id|
|body|string|true|none|Your message.|
|to|string|true|none|Recipient phone number in <a href="https://en.wikipedia.org/wiki/E.164" rel="noopener" target="_blank">E.164</a> format.|
|source|string|false|none|Your method of sending e.g. 'wordpress', 'php', 'c#'.|
|schedule|integer(int32)|false|none|Leave blank for immediate delivery. Your schedule time in unix format http://help.clicksend.com/what-is-a-unix-timestamp|
|custom_string|string|false|none|Your reference. Will be passed back with all replies and delivery reports.|
|list_id|integer(int32)|false|none|Your list ID if sending to a whole list. Can be used instead of 'to'.|
|country|string|false|none|ISO alpha-2 character country code e.g. 'US', we use this to format the recipient number if it's not in international format.|
|from_email|string|false|none|An email address where the reply should be emailed to. If omitted, the reply will be emailed back to the user who sent the outgoing SMS.|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request post"></span>Calculate SMS Price

> Code samples

```shell
curl --include \
     --request POST \
     --header "Content-Type: application/json" \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
     --data-binary "    {
        \"messages\":[
            {
                \"source\":\"php\",
                \"from\":\"sendmobile\",
                \"body\":\"Jelly liquorice marshmallow candy carrot cake 4Eyffjs1vL.\",
                \"to\":\"+61411111111\",
                \"schedule\":1436874701,
                \"custom_string\":\"this is a test\"
            },
            {
                \"source\":\"php\",
                \"from\":\"sendlist\",
                \"body\":\"Chocolate bar icing icing oat cake carrot cake jelly cotton MWEvciEPIr.\",
                \"list_id\":428,
                \"schedule\":1436876011,
                \"custom_string\":\"this is a test\"
            }
        ]
    }" \
'https://rest.clicksend.com/v3/sms/price'
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/price");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POST, TRUE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"messages\": [
    {
      \"source\": \"php\",
      \"from\": \"sendmobile\",
      \"body\": \"Jelly liquorice marshmallow candy carrot cake 4Eyffjs1vL.\",
      \"to\": \"+61411111111\",
      \"schedule\": 1436874701,
      \"custom_string\": \"this is a test\"
    },
    {
      \"source\": \"php\",
      \"from\": \"sendlist\",
      \"body\": \"Chocolate bar icing icing oat cake carrot cake jelly cotton MWEvciEPIr.\",
      \"list_id\": 428,
      \"schedule\": 1436876011,
      \"custom_string\": \"this is a test\"
    }
  ]
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/json",
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "messages": [
    {
      "schedule": 0,
      "country": "country",
      "from_email": "from_email",
      "list_id": 0,
      "from": "from",
      "to": "69505609",
      "source": "sdk",
      "body": "body",
      "custom_string": "custom_string"
    },
    {
      "schedule": 0,
      "country": "country",
      "from_email": "from_email",
      "list_id": 0,
      "from": "from",
      "to": "69505609",
      "source": "sdk",
      "body": "body",
      "custom_string": "custom_string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://rest.clicksend.com/v3/sms/price',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://rest.clicksend.com/v3/sms/price',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://rest.clicksend.com/v3/sms/price', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/price");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://rest.clicksend.com/v3/sms/price", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Body parameter

```json
{
  "messages": [
    {
      "schedule": 0,
      "country": "country",
      "from_email": "from_email",
      "list_id": 0,
      "from": "from",
      "to": "69505609",
      "source": "sdk",
      "body": "body",
      "custom_string": "custom_string"
    },
    {
      "schedule": 0,
      "country": "country",
      "from_email": "from_email",
      "list_id": 0,
      "from": "from",
      "to": "69505609",
      "source": "sdk",
      "body": "body",
      "custom_string": "custom_string"
    }
  ]
}
```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Here are your data.",
  "data": {
    "total_price": 0.2264,
    "total_count": 1,
    "queued_count": 1,
    "messages": [
      {
        "to": "+61411111111",
        "body": "Jelly liquorice marshmallow candy carrot cake 4Eyffjs1vL.",
        "from": "sendmobile",
        "schedule": 1436874701,
        "message_parts": 1,
        "message_price": "0.0566",
        "custom_string": "this is a test",
        "country": "AU",
        "status": "SUCCESS"
      }
    ]
  }
}  
```

<span class="method post"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/price</span>

*Calculate sms price*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|from|string|true|[yes](http://help.clicksend.com/SMS/what-is-a-sender-id-or-sender-number)|Your sender id|
|body|string|true|none|Your message.|
|to|string|true|none|Recipient phone number in <a href="https://en.wikipedia.org/wiki/E.164" rel="noopener" target="_blank">E.164</a> format.|
|source|string|false|none|Your method of sending e.g. 'wordpress', 'php', 'c#'.|
|schedule|integer(int32)|false|none|Leave blank for immediate delivery. Your schedule time in unix format http://help.clicksend.com/what-is-a-unix-timestamp|
|custom_string|string|false|none|Your reference. Will be passed back with all replies and delivery reports.|
|list_id|integer(int32)|false|none|Your list ID if sending to a whole list. Can be used instead of 'to'.|
|country|string|false|none|ISO alpha-2 character country code e.g. 'US', we use this to format the recipient number if it's not in international format.|
|from_email|string|false|none|An email address where the reply should be emailed to. If omitted, the reply will be emailed back to the user who sent the outgoing SMS.|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request get"></span>Export SMS History

> Code samples

```shell
curl --include \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
'https://rest.clicksend.com/v3/sms/history/export?filename={filename}'
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/history/export?filename={filename}");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://rest.clicksend.com/v3/sms/history/export?filename=string',
{
  method: 'GET'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.get 'https://rest.clicksend.com/v3/sms/history/export',
  params: {
  'filename' => 'string'
}

p JSON.parse(result)

```

```python
import requests

r = requests.get('https://rest.clicksend.com/v3/sms/history/export', params={
  'filename': 'string'
)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/history/export?filename=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://rest.clicksend.com/v3/sms/history/export", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Download your file here.",
  "data": {
    "url": "https://rest.clicksend.com/files/22D55AF9-6CF0-476D-A8B3-82A998FD2738?filename=export.csv"
  }
}
```

<span class="method get"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/history/export</span>

*Export all sms history*

<h3 id="smshistoryexportget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|filename|query|string|true|Filename to download history as|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request get"></span>View SMS Receipts

> Code samples

```shell
curl --include \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
'https://rest.clicksend.com/v3/sms/receipts'
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/receipts");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://rest.clicksend.com/v3/sms/receipts',
{
  method: 'GET'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.get 'https://rest.clicksend.com/v3/sms/receipts',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.get('https://rest.clicksend.com/v3/sms/receipts', params={

)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/receipts");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://rest.clicksend.com/v3/sms/receipts", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Here are your delivery receipts.",
  "data": {
    "total": 3,
    "per_page": 15,
    "current_page": 1,
    "last_page": 1,
    "next_page_url": null,
    "prev_page_url": null,
    "from": 1,
    "to": 3,
    "data": [
      {
        "timestamp_send": "1442381791",
        "timestamp": "1442381791",
        "message_id": "31BC271B-1E0C-45F6-9E7E-97186C46BB82",
        "status_code": "201",
        "status_text": "Success: Message received on handset.",
        "error_code": null,
        "error_text": null,
        "custom_string": null,
        "_message_type": "sms"
      },
      {
        "timestamp_send": "1442381829",
        "timestamp": "1442381829",
        "message_id": "23C8ADA3-FD8B-420B-801A-F829BB87AC6F",
        "status_code": "201",
        "status_text": "Success: Message received on handset.",
        "error_code": null,
        "error_text": null,
        "custom_string": null,
        "_message_type": "sms"
      },
      {
        "timestamp_send": "1442381861",
        "timestamp": "1442381861",
        "message_id": "3BD22FAD-A5D3-4D99-B4C0-16BF65BE052C",
        "status_code": "201",
        "status_text": "Success: Message received on handset.",
        "error_code": null,
        "error_text": null,
        "custom_string": null,
        "_message_type": "sms"
      }
    ]
  }
}
```

<span class="method get"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/receipts</span>

*Get all delivery receipts*

### **Push Delivery Receipts**

If you prefer, we can push message replies to your server as they arrive with us.

1. Log into your account.
2. Click on 'SMS' then 'Settings' tab.
3. Click on the 'SMS Delivery Report Settings' menu.
4. Select 'Forward to URL'.
5. Enter the URL and click 'Save'.


The following variables will be posted to the URL specified:

| Variable | Description |
|---|---|
| `timestamp_send` | Timestamp of the original send request in UNIX format. e.g 1439173980
| `timestamp` | Timestamp of delivery report in UNIX format. e.g 1439173981
| `message_id` | Message ID, returned when originally sending the message.
| `status` | Delivered or Undelivered
| `status_code` | Status code. Refer to 'SMS Delivery Status Codes' in docs.
| `status_text` | Status text.
| `error_code` | Error code.
| `error_text` | Error text.
| `custom_string` | A custom string used when sending the original message.
| `user_id` | The user ID of the user who sent the message.
| `subaccount_id` | The subaccount ID of the user who sent the message.
| `message_type` | 'sms' (constant).




### **Pull Delivery Receipts**

Receive delivery reports by polling.
You can poll our server and retrieve delivery reports at a time that suits you.

1. Log into your account.
2. Click on 'SMS' then 'Settings' tab.
3. Click on the 'SMS Delivery Report Settings' menu.
4. Select 'Poll our server' and click 'Save'.

<h3 id="smsreceiptsget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|integer(int32)|false|[Page number](#pagination)|
|limit|query|integer(int32)|false|[Number of records per page](#pagination)|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request post"></span>Create Test SMS Receipt

> Code samples

```shell
curl --include \
     --request POST \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
     --header "Content-Type: application/json" \
     --data-binary "    {
        \"url\":\"http://yourdomain.com\"
    }" \
'https://rest.clicksend.com/v3/sms/receipts'
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/receipts");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POST, TRUE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"url\": \"http://yourdomain.com\"
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/json",
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = 'string';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://rest.clicksend.com/v3/sms/receipts',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://rest.clicksend.com/v3/sms/receipts',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://rest.clicksend.com/v3/sms/receipts', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/receipts");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://rest.clicksend.com/v3/sms/receipts", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Body parameter

```json
{
  "url":"http://yourdomain.com"
}
```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Receipt has been added",
  "data": {
    "timestamp": "1441958441",
    "message_id": "493FFB41-9733-4641-985F-BD79A067B58F",
    "status_code": "201",
    "status_text": "Success: Message received on handset.",
    "error_code": null,
    "error_text": null,
    "custom_string": null
  }
}
```

<span class="method post"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/receipts</span>

*Add a delivery receipt*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|url|string|true|none|Your URL that you want to forward to.|


Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request put"></span>Mark SMS Receipt As Read

> Code samples

```shell
curl --include \
     --request PUT \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
     --header "Content-Type: application/json" \
     --data-binary "{
    \"date_before\": 1441958441
}" \
'https://rest.clicksend.com/v3/sms/receipts-read'
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/receipts-read");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PUT");

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"date_before\": 1441958441
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/json",
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = 'string';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://rest.clicksend.com/v3/sms/receipts-read',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.put 'https://rest.clicksend.com/v3/sms/receipts-read',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.put('https://rest.clicksend.com/v3/sms/receipts-read', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/receipts-read");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://rest.clicksend.com/v3/sms/receipts-read", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Body parameter

```json
{
  "date_before": 1441958441
}
```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Receipts has been marked as read.",
  "data": []
}
```

<span class="method put"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/receipts-read</span>

*Mark delivery receipts as read*

<h3 id="smsreceiptsreadput-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|date_before|body|string|false|Mark all as read before this timestamp|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request get"></span>View Inbound SMS

> Code samples

```shell
curl --include \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
'https://rest.clicksend.com/v3/sms/inbound'
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/inbound");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://rest.clicksend.com/v3/sms/inbound',
{
  method: 'GET'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.get 'https://rest.clicksend.com/v3/sms/inbound',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.get('https://rest.clicksend.com/v3/sms/inbound', params={

)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/inbound");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://rest.clicksend.com/v3/sms/inbound", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Here are your data.",
  "data": {
    "total": 3,
    "per_page": 15,
    "current_page": 1,
    "last_page": 1,
    "next_page_url": null,
    "prev_page_url": null,
    "from": 1,
    "to": 3,
    "data": [
      {
        "timestamp": "1436174407",
        "from": "+61411111111",
        "body": "Liquorice sweet roll fruitcake gummies. ",
        "original_body": "Liquorice sweet roll fruitcake gummies. ",
        "original_message_id": "C557B56E-83C0-4070-A74C-9BF05474B418",
        "to": "SC557B56E-83C0-4070-A74C-9BF05474B418",
        "custom_string": "22PKU978RF",
        "message_id": "C557B56E-83C0-4070-A74C-9BF05474B418",
        "_keyword": "liquorice"
      },
      {
        "timestamp": "1436174406",
        "from": "Lemon drops brownie pie chocolate bar pie swe",
        "body": "Lemon drops brownie pie chocolate bar pie sweet jelly-o chocolate.",
        "original_body": "Lemon drops brownie pie chocolate bar pie sweet jelly-o chocolate.",
        "original_message_id": "373F7121-8089-42FA-8F5C-8F8F7C18DFAA",
        "to": "S373F7121-8089-42FA-8F5C-8F8F7C18DFAA",
        "custom_string": "2ATQKLETYX",
        "message_id": "C557B56E-83C0-4070-A74C-9BF05474B418",
        "_keyword": "lemon"
      },
      {
        "timestamp": "1436174405",
        "from": "Jelly beans jelly cupcake bear claw gummies.",
        "body": "Jelly beans jelly cupcake bear claw gummies.",
        "original_body": "Jelly beans jelly cupcake bear claw gummies.",
        "original_message_id": "A9F3863C-D88E-4A54-BEF1-BD73A6E42E2E",
        "to": "SA9F3863C-D88E-4A54-BEF1-BD73A6E42E2E",
        "custom_string": "0PZCOGJP0A",
        "message_id": "C557B56E-83C0-4070-A74C-9BF05474B418",
        "_keyword": "jelly"
      }
    ]
  }
}
```

<span class="method get"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/inbound</span>

*Get all inbound sms*

### **Push Inbound SMS**

If you prefer, we can push message replies to your server as they arrive with us.

1. Log into your account.
2. Click on 'SMS' then 'Settings' tab.
3. Click on the 'Inbound SMS Settings' menu.
4. Add a new rule to and select Action: 'URL'.
5. Enter the URL and click 'Save'.

The following variables will be posted to the URL specified:

| Variable | Description |
|---|---|
| `timestamp` | Timestamp in UNIX format. e.g 1439173981
| `to` | Number that the SMS was sent to (your Dedicated or shared number).
| `from` | Recipient Mobile Number that sent the reply message.
| `body` | Inbound message body.
| `original_body` | Original outgoing SMS message body.
| `original_message_id` | Original SMS message ID. Returned when originally sending the message.
| `custom_string` | A custom string used when sending the original message.
| `user_id` | The user ID of the user who sent the message.
| `subaccount_id` | The subaccount ID of the user who sent the message.
| `message_id` | The Message ID for the inbound message.

Note: HTTP `POST` is used to send the variables (not `GET` or query-string). [**More Info**](http://www.w3schools.com/tags/ref_httpmethods.asp).

Your URL should respond with a 200 OK HTTP status code. If we receive a non-200 response or your URL is down/times out, we will continue to retry every minute until we reach 10 retries. After 10 attempts, we'll mark it as completed. If your server is down for a long period of time, we can manually re-queue the data.

### **Pull Inbound SMS**

Receive SMS by polling your Inbox.
You can poll our server and retrieve new Messages at a time that suits you.

1. Log into your account.
2. Click on 'SMS' then 'Settings' tab.
3. Click on the 'Inbound SMS Settings' menu.
4. Select Action: 'POLL' and click 'Save'.


<h3 id="smsinboundget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|integer(int32)|false|[Page number](#pagination)|
|limit|query|integer(int32)|false|[Number of records per page](#pagination)|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request post"></span>Create Test Inbound SMS

> Code samples

```shell
curl --include \
     --request POST \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
     --header "Content-Type: application/json" \
     --data-binary "    {
        \"url\":\"http://yourdomain.com\"
    }" \
'https://rest.clicksend.com/v3/sms/inbound'
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/inbound");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POST, TRUE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"url\": \"http://yourdomain.com\"
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/json",
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = 'string';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://rest.clicksend.com/v3/sms/inbound',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://rest.clicksend.com/v3/sms/inbound',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://rest.clicksend.com/v3/sms/inbound', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/inbound");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://rest.clicksend.com/v3/sms/inbound", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```
> Body parameter

```json
{
  "url":"http://yourdomain.com"
}
```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Here are your incoming messages.",
  "data": {
    "timestamp": "1442398236",
    "from": "+61468460249",
    "body": "This is a test incoming SMS. 5IHHOWWZTB.",
    "original_body": "This is the original message. AA4NN45X7J.",
    "original_message_id": "F35B6DF1-0C9E-488F-954E-2F603B6192F5",
    "to": "+61411111111",
    "custom_string": null,
    "message_id": "C557B56E-83C0-4070-A74C-9BF05474B418",
    "_keyword": "this"
  }
}
```

<span class="method post"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/inbound</span>

*Create inbound sms*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|url|string|true|none|Your URL that you want to forward to.|


Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request put"></span>Cancel SMS

> Code samples

```shell
curl --include \
     --request PUT \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
'https://rest.clicksend.com/v3/sms/{message_id}/cancel'
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/{message_id}/cancel");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PUT");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://rest.clicksend.com/v3/sms/{message_id}/cancel',
{
  method: 'PUT'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.put 'https://rest.clicksend.com/v3/sms/{message_id}/cancel',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.put('https://rest.clicksend.com/v3/sms/{message_id}/cancel', params={

)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/{message_id}/cancel");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://rest.clicksend.com/v3/sms/{message_id}/cancel", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Message 307EF035-B7CE-4321-93CD-0753597B7293 has been cancelled.",
  "data": []
}
```

<span class="method put"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/<span class="parameter">{message_id}</span>/cancel</span>

*Update scheduled message as cancelled*

<h3 id="smscancelbymessageidput-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|message_id|path|string|true|The message ID you want to cancel|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request put"></span>Cancel All SMS

> Code samples

```shell
curl --include \
     --request PUT \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
'https://rest.clicksend.com/v3/sms/cancel-all'
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/cancel-all");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PUT");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://rest.clicksend.com/v3/sms/cancel-all',
{
  method: 'PUT'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.put 'https://rest.clicksend.com/v3/sms/cancel-all',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.put('https://rest.clicksend.com/v3/sms/cancel-all', params={

)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/cancel-all");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://rest.clicksend.com/v3/sms/cancel-all", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "5 messages has been cancelled.",
  "data": {
    "count": 5
  }
}
```

<span class="method put"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/cancel-all</span>

*Update all scheduled message as cancelled*

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request get"></span>View SMS Templates

> Code samples

```shell
curl --include \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
'https://rest.clicksend.com/v3/sms/templates'
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/templates");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://rest.clicksend.com/v3/sms/templates',
{
  method: 'GET'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.get 'https://rest.clicksend.com/v3/sms/templates',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.get('https://rest.clicksend.com/v3/sms/templates', params={

)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/templates");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://rest.clicksend.com/v3/sms/templates", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Here are your data.",
  "data": {
    "total": 2,
    "per_page": 15,
    "current_page": 1,
    "last_page": 1,
    "next_page_url": null,
    "prev_page_url": null,
    "from": 1,
    "to": 2,
    "data": [
      {
        "template_id": 1,
        "body": "This is a sample template.",
        "template_name": "My Awesome Template"
      },
      {
        "template_id": 2,
        "body": "This is my second sample template.",
        "template_name": "My Awesome Template 2"
      }
    ]
  }
}
```

<span class="method get"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/templates</span>

*Get lists of all sms templates*

<h3 id="smstemplatesget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|integer(int32)|false|[Page number](#pagination)|
|limit|query|integer(int32)|false|[Number of records per page](#pagination)|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request post"></span>Create SMS Template

> Code samples

```shell
curl --include \
     --request POST \
     --header "Content-Type: application/json" \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
     --data-binary "    {
        \"template_name\":\"Template 501916\",
        \"body\":\"This is a sample content: H7YI68B3yk for this template.\"
    }" \
'https://rest.clicksend.com/v3/sms/templates'
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/templates");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POST, TRUE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"template_name\": \"Template 501916\",
  \"body\": \"This is a sample content: H7YI68B3yk for this template.\"
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/json",
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "template_name": "template_name",
  "body": "body"
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://rest.clicksend.com/v3/sms/templates',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://rest.clicksend.com/v3/sms/templates',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://rest.clicksend.com/v3/sms/templates', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/templates");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://rest.clicksend.com/v3/sms/templates", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Body parameter

```json
{
  "template_name": "template_name",
  "body": "body"
}
```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "New template has been saved.",
  "data": {
    "template_id": 25,
    "body": "This is a sample content: H7YI68B3yk for this template.",
    "template_name": "Template 501916"
  }
}
```

<span class="method post"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/templates</span>

*Create sms template*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|template_name|string|true|none|Name of template|
|body|string|true|none|Body of template|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request put"></span>Update SMS Template

> Code samples

```shell
curl --include \
     --request PUT \
     --header "Content-Type: application/json" \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
     --data-binary "    {
        \"template_name\":\"I am updated\",
        \"body\":\"This is a sample content: Sc0KNWgSMG for this template.\"
    }" \
'https://rest.clicksend.com/v3/sms/templates/{template_id}'
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/templates/{template_id}");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PUT");

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"template_name\": \"I am updated\",
  \"body\": \"This is a sample content: Sc0KNWgSMG for this template.\"
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/json",
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "template_name": "template_name",
  "body": "body"
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://rest.clicksend.com/v3/sms/templates/{template_id}',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.put 'https://rest.clicksend.com/v3/sms/templates/{template_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.put('https://rest.clicksend.com/v3/sms/templates/{template_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/templates/{template_id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://rest.clicksend.com/v3/sms/templates/{template_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Body parameter

```json
{
  "template_name": "template_name",
  "body": "body"
}
```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Your template has been updated.",
  "data": {
    "template_id": 25,
    "body": "This is a sample content: Sc0KNWgSMG for this template.",
    "template_name": "I am updated"
  }
}
```

<span class="method put"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/templates/<span class="parameter">{template_id}</span></span>

*Update sms template*

<h3 id="smstemplatesbytemplateidput-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|template_id|path|integer(int32)|true|Template id|

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|template_name|string|true|none|Name of template|
|body|string|true|none|Body of template|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request delete"></span>Delete SMS Template

> Code samples

```shell
curl --include \
     --request DELETE \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
'https://rest.clicksend.com/v3/sms/templates/{template_id}'
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/templates/{template_id}");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "DELETE");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://rest.clicksend.com/v3/sms/templates/{template_id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.delete 'https://rest.clicksend.com/v3/sms/templates/{template_id}',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.delete('https://rest.clicksend.com/v3/sms/templates/{template_id}', params={

)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/templates/{template_id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://rest.clicksend.com/v3/sms/templates/{template_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Your template has been deleted.",
  "data": []
}
```

<span class="method delete"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/templates/<span class="parameter">{template_id}</span></span>

*Delete sms template*

<h3 id="smstemplatesbytemplateiddelete-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|template_id|path|integer(int32)|true|Template id|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request put"></span>Mark Inbound SMS As Read

> Code samples

```shell
curl --include \
     --request PUT \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
     --header "Content-Type: application/json" \
     --data-binary "    {
        \"date_before\":1442398100
    }" \
'https://rest.clicksend.com/v3/sms/inbound-read'

```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/inbound-read");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PUT");

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"date_before\": 1442398100
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/json",
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = 'string';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://rest.clicksend.com/v3/sms/inbound-read',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.put 'https://rest.clicksend.com/v3/sms/inbound-read',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.put('https://rest.clicksend.com/v3/sms/inbound-read', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/inbound-read");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://rest.clicksend.com/v3/sms/inbound-read", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Inbound messages have been marked as read.",
  "data": []
}
```

<span class="method put"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/inbound-read</span>

*Mark inbound SMS as read*

Mark all inbound SMS as read optionally before a certain date

<h3 id="smsinboundreadput-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|date_before|body|string|false|An optional timestamp - mark all as read before this timestamp. If not given, all messages will be marked as read.|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request get"></span>View Specific SMS Receipt

> Code samples

```shell
curl --include \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
'https://rest.clicksend.com/v3/sms/receipts/{message_id}'

```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/receipts/{message_id}");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://rest.clicksend.com/v3/sms/receipts/{message_id}',
{
  method: 'GET'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.get 'https://rest.clicksend.com/v3/sms/receipts/{message_id}',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.get('https://rest.clicksend.com/v3/sms/receipts/{message_id}', params={

)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/receipts/{message_id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://rest.clicksend.com/v3/sms/receipts/{message_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Your receipt.",
  "data": {
    "timestamp_send": "1450854013",
    "timestamp": "1451200622",
    "message_id": "88AB118E-EB1B-478C-98CE-6C73ABA23F67",
    "status_code": "Completed",
    "status_text": "statustext",
    "error_code": "errorcode",
    "error_text": "errortext",
    "custom_string": "",
    "message_type": "sms"
  }
}
```

<span class="method get"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/receipts/<span class="parameter">{message_id}</span></span>

*Get a Specific Delivery Receipt*

<h3 id="smsreceiptsbymessageidget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|message_id|path|string|true|Message ID|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>

## <span class="request get"></span>View SMS History

> Code samples

```shell
curl --include \
     --header "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA==" \
'https://rest.clicksend.com/v3/sms/history?date_from=&date_to='
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://rest.clicksend.com/v3/sms/history?date_from=&date_to=");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Authorization: Basic YXBpLXVzZXJuYW1lOmFwaS1wYXNzd29yZA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://rest.clicksend.com/v3/sms/history',
{
  method: 'GET'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.get 'https://rest.clicksend.com/v3/sms/history',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.get('https://rest.clicksend.com/v3/sms/history', params={

)

print r.json()

```

```java
URL obj = new URL("https://rest.clicksend.com/v3/sms/history");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://rest.clicksend.com/v3/sms/history", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

> Response

```json
{
  "http_code": 200,
  "response_code": "SUCCESS",
  "response_msg": "Here are your data.",
  "data": {
    "total": 1,
    "per_page": 15,
    "current_page": 1,
    "last_page": 1,
    "next_page_url": null,
    "prev_page_url": null,
    "from": 1,
    "to": 1,
    "data": [
      {
        "direction": "out",
        "date": "1436932432",
        "to": "+16783270696",
        "body": "Chocolate bar icing icing oat cake carrot cake jelly cotton 1iQByXxdLN.",
        "status": "Completed",
        "from": "sendlist",
        "schedule": "1436879372",
        "status_code": null,
        "status_text": null,
        "error_code": null,
        "error_text": null,
        "message_id": "4E90F4C3-43A3-489D-9AB8-DA1F4332A0C3",
        "message_parts": "1.00",
        "message_price": "0.070000",
        "from_email": null,
        "list_id": null,
        "custom_string": "this is a test",
        "contact_id": 0,
        "user_id": 1,
        "subaccount_id": 1,
        "country": "US",
        "carrier": "",
        "first_name": "John",
        "last_name": "Doe",
        "_api_username": "johndoe"
      }
    ]
  }
}
```

<span class="method get"></span>  <span class="definition" >https://rest.clicksend.com/v3/sms/history</span>

*Get all sms history*

<h3 id="smshistoryget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|date_from|query|integer(int32)|false|Start date|
|date_to|query|integer(int32)|false|End date|
|page|query|integer(int32)|false|[Page number](#pagination)|
|limit|query|integer(int32)|false|[Number of records per page](#pagination)|

Refer to [Status Codes](#status-codes) for definitions of HTTP status code responses.

<aside class="warning">
This endpoint requires authentication, <a href="#authentication">more info...</a>
</aside>
