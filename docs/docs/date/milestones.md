# Milestone Dates (Beta)

This API Endpoint will provide data regarding significant milestones in the Islamic Calendar

## Support
At the moment, this feature will only use data provided by the Wifaqul Ulama Calendar

## Request

```http
GET https://api.wifaqululama.co.uk/hijri/v2/milestones
```

## Response
```http
HTTP/1.1 200 OK
Date: Sat, 20 Nov 2021 20:29:36 GMT
Content-Type: text/json; charset=UTF-8
```
```json

{
  "year": [{
    "ce": "2021",
    "months": [["15/01","06/1442"],["14/02","07/1442"],["15/03","08/1442"],["14/04","09/1442"],["13/05","10/1442"],["12/06","11/1442"],["12/07","12/1442"],["10/08","01/1443"],["09/09","02/1443"],["08/10","03/1443"],["07/11","04/1443"],["06/12","05/1443"]]
  }]
}
```