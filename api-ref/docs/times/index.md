# Salah Times

The API can be used to get salah times for any location on Earth and can be also be configured with a variety of options.

It is based on the Adhan Salah Time Library but also provides additional features to calculate times at higher altitudes such as the UK.

## Request

```http
GET https://api.wifaqululama.co.uk/times/v1
```

```json
{
  "location": {
    "latitude": 51,
    "longitude": 50
  },
  "date": {
    "year": 2021,
    "month": 11,
    "day": 21
  },
  "dateFrom": null,
  "dateTo": null,
  "format": "HH:mm",
  "madhab": "HANAFI",
  "calculationMethod": "KARACHI",
  "highLatitudeRule": "WIFAQ",
  "fajrAqrabulAyyam": false
}
```

### Location
- `latitude`: Latitude
- `longitude`: Longitude

### Date
A simple date object with the year, month and day

#### Date From and Date To
When `dateFrom` and `dateTo` are not null, the response will return times for all days specified

### Madhab
| Value | Description |
| ----- | ----------- |
| `SHAFI` | Earlier Asr time |
| `HANAFI` | Later Asr time |

**Default**: `HANAFI`

### Calculation Method
| Value | Description |
| ----- | ----------- |
| `MUSLIM_WORLD_LEAGUE` | Muslim World League. Fajr angle: 18, Isha angle: 17 |
| `EGYPTIAN` | Egyptian General Authority of Survey. Fajr angle: 19.5, Isha angle: 17.5 |
| `KARACHI` | University of Islamic Sciences, Karachi. Fajr angle: 18, Isha angle: 18 |
| `UMM_AL_QURA` | Umm al-Qura University, Makkah. Fajr angle: 18, Isha interval: 90. *Note: you should add a +30 minute custom adjustment for Isha during Ramadan.* |
| `DUBAI` | Method used in UAE. Fajr and Isha angles of 18.2 degrees. |
| `QATAR` | Modified version of Umm al-Qura used in Qatar. Fajr angle: 18, Isha interval: 90. |
| `KUWAIT` | Method used by the country of Kuwait. Fajr angle: 18, Isha angle: 17.5 |
| `MOONSIGHTING_COMMITTEE` | Moonsighting Committee. Fajr angle: 18, Isha angle: 18. Also uses seasonal adjustment values. |
| `SINGAPORE` | Method used by Singapore. Fajr angle: 20, Isha angle: 18. |
| `NORTH_AMERICA` | Referred to as the ISNA method. This method is included for completeness but is not recommended. Fajr angle: 15, Isha angle: 15 |
| `KUWAIT` | Kuwait. Fajr angle: 18, Isha angle: 17.5 |
| `OTHER` | Fajr angle: 0, Isha angle: 0. This is the default value for `method` when initializing a `CalculationParameters` object. |

**Default**: `KARACHI`

### High Latitude Rule

| Value | Description |
| ----- | ----------- |
| `MIDDLE_OF_THE_NIGHT` | Fajr will never be earlier than the middle of the night and Isha will never be later than the middle of the night |
| `SEVENTH_OF_THE_NIGHT` | Fajr will never be earlier than the beginning of the last seventh of the night and Isha will never be later than the end of the first seventh of the night |
| `TWILIGHT_ANGLE` | Similar to `SEVENTH_OF_THE_NIGHT`, but instead of 1/7, the fraction of the night used is fajrAngle/60 and ishaAngle/60 |
| `WIFAQ` | Isha will match `SEVENTH_OF_THE_NIGHT` and Fajr will match `MIDDLE_OF_THE_NIGHT` |

**Default**: `WIFAQ`

### Aqrabul Ayyam (UK Only)
This boolean value will determine if the API should use Aqrabul Ayyam Calculations for Fajr instead of `MIDDLE_OF_THE_NIGHT` during perpetual twilight. The `WIFAQ` option must also be used for `highLatitudeRule`

### Response
```http
HTTP/1.1 200 OK
Date: Sat, 20 Nov 2021 20:29:36 GMT
Content-Type: text/json; charset=UTF-8
```

```json
[
  {
    "date": {
      "year": 2021,
      "month": 11,
      "day": 21
    },
    "fajr": "05:39",
    "sunrise": "07:41",
    "zuhr": "11:59",
    "asr": "14:18",
    "maghrib": "16:12",
    "isha": "17:48"
  }
]
```