# Luxembourg Population Data Service
This web service delivers population data for Luxembourg for a given year using the Statec API. It can provide the total population, gender-specific statistics, and a breakdown between Luxembourgish and foreign residents. If data for the requested year is unavailable, the service will return the nearest years for which data exists

# How to Use the Service
The service is accessible via a single HTTP GET endpoint. 
- Directly in your browser – just enter the URL with the desired year
- Using curl in the command line
# Endpoint
**`GET /api/population/{year}`**

Example
- If data for the requested year is available
**`GET http://localhost:8080/api/population/2024`**
```json
{
  "after": null,
  "before": null,
  "data": {
    "foreign_female": 154079,
    "foreign_male": 163599,
    "luxembourgish_female": 179697,
    "luxembourgish_male": 174675,
    "total": 672050,
    "total_female": 333776,
    "total_male": 338274,
    "year": 2024
  },
  "requestedYear": 2024
}
```
- If data for the requested year is unavailable
 
**`GET http://localhost:8080/api/population/1823`**
```json
{
  "after": {
    "foreign_female": 0,
    "foreign_male": 0,
    "luxembourgish_female": 0,
    "luxembourgish_male": 0,
    "total": 175223,
    "total_female": 0,
    "total_male": 0,
    "year": 1839
  },
  "before": {
    "foreign_female": 0,
    "foreign_male": 0,
    "luxembourgish_female": 0,
    "luxembourgish_male": 0,
    "total": 134082,
    "total_female": 0,
    "total_male": 0,
    "year": 1822
  },
  "data": null,
  "requestedYear": 1823
}
```

# Error Handling
- Invalid year format (not a number)
```json
{
  "error": "Invalid year format: '202w'. Please enter a nmber"
}
```
- Year out of range
```json
{
  "error": "No information for the specified year.Please enter a year between 1821 and 2024"
}
```
