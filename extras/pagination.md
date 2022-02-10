## Pagination

We are using ES' built in pagination where the user can set per query the size and the page of the result list.  
We currently have an upper limit of 250 results per page. 
```
{
  object(size: 250, page:2){
    id
    summary
  }
}
```
More detailed information can be found in the response's extension block:
```
"extensions": {
  "pagination": {
    "hits": 196951,
    "per_page": 250,
    "current_page": 2,
    "number_of_pages": 788
  }
}
```