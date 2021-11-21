# Hijri Date API

The new Hijri Date API improves the capability and flexibility over the legacy API and is highly recommended.

## Request

```http
GET https://api.wifaqululama.co.uk/hijri/v2/{responseFormat}
```

### Request Options

This API permits additional configuration options to be passed along with the request

#### ResponseFormat

The endpoint also takes an optional parameter which will allow you to define the type of response object received from the server.

##### Options

| Parameter      | Description                          |
| ----------- | ------------------------------------ |
| `raw`       | Will return a raw date object  |
| `formatted`       | Will return a date formatted using `SimpleDateFormat`  |

#### Raw Date Request

##### Request

```json
{
  "requestData": {
    "date": {
      "year": 2021,
      "month": 11,
      "day": 20
    },
    "locale": "GB"
  }
}
```

| Parameter      | Description                          |
| ----------- | ------------------------------------ |
| `date`       | Date to be used for the request. If not provided, the date of the server (UK) will be used   |
| `locale`    | The country code for the request. See [Supported Countries](suppoted-countries.md) For information on how this information is processed |

#### Formatted Date Request
##### Request

```json
{
  "requestData": {
    "date": {
      "year": 2021,
      "month": 11,
      "day": 20
    },
    "format": "dd/LLLL/YYYY",
    "locale": "GB",
    "language": "en"
  }
}
```

| Parameter      | Description                          |
| ----------- | ------------------------------------ |
| `date`       | Date to be used for the request. If not provided, the date of the server (UK) will be used   |
| `format`       | Format of the response using `SimpleDateFormat` rules  |
| `locale`    | The country code for the request. See [Supported Countries](suppoted-countries.md) For information on how this information is processed |
| `language`    | The language code for the response data. |

##### Response
```http
HTTP/1.1 200 OK
Date: Sat, 20 Nov 2021 20:29:36 GMT
Content-Type: text/json; charset=UTF-8
```

```json
{
  "date": "15/Rabi-II/1443"
}
```

### Error Codes

| Code      | Reason                          |
| ----------- | ------------------------------------ |
| `404`       | Unable to lookup date information. (It might be too far in the past or future)  |
