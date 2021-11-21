# Legacy Date API

This API will provide compatibility with the legacy Hijri Date API via the following endpoint:

## Request 

```http
GET https://api.wifaqululama.co.uk/hijri/v1/
```

## Response
```http
HTTP/1.1 200 OK
Date: Sat, 20 Nov 2021 20:29:36 GMT
Content-Type: text/json; charset=UTF-8
```
```json
{
   "gregorian":[
      "Saturday",
      "20",
      "11",
      "2021"
   ],
   "islamic":[
      "15",
      "Rabi ath-Thani",
      "1443"
   ]
}
```

