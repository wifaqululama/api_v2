# Qibla

The API also provides an endpoint to get the qibla direction

## Request

```http 
GET https://api.wifaqululama.co.uk/qibla/v1/{latitude}/{longitude}
```

## Response
```http
HTTP/1.1 200 OK
Date: Sat, 20 Nov 2021 20:29:36 GMT
Content-Type: text/json; charset=UTF-8
```
```json
{
  "qiblaDirection": 117.5
}
```