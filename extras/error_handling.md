## Error Handling
- For protection against malicious queries the maximum query depth is set to 2 for nested queries.
```
{
  "message": "'anonymous' exceeds maximum operation depth of 2.",
}
```
- Exceeding the rate limit for requests,
```
{
  "message": "API rate limit exceeded"
}
```
- Sending a request with an invalid api key.
```
{
  "message":
    {
      "reason":"API Key Invalid"
      "status_code":403
    }
}
```
- Attempting to use an aggregation term that is not accepted.
```
{
      "message": "error test is not a valid key! Please use these keys: ['classification', 'culture', 'datatype', 'department', 'departmentId', 'maker', 'material', 'period', 'place']"
}
```