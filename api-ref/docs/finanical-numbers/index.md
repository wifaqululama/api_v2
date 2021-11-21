# Financial Numbers

This API can be used to get Islamic Financial Numbers

## Request

```http
GET https://api.wifaqululama.co.uk/financial/v1/
```

## Response
```http
HTTP/1.1 200 OK
Date: Sat, 20 Nov 2021 20:29:36 GMT
Content-Type: text/json; charset=UTF-8
```
```json
{
  "currency": "GBP",
  "gold": {
    "gram": 42.10,
    "zakaah": 3682.91
  },
  "silver": {
    "gram": "0.55",
    "zakaah": 336.80,
    "mahr-m": 17.05,
    "mahr-f": 841.50
  }
}
```

| Value      | Description                          |
| ----------- | ------------------------------------ |
| `currency`       | The Currency the provided data is in |
| `gold`       | Values based on the gold price |
| `gram`       | Price per gram of an element |
| `zakaah`       | The Zakaah Nisab Value |
| `mahr-m`       | The minimum Mahr |
| `mahr-f`       | Mahr Fatimi  |
