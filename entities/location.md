
### Location

#### Fields
These are all the fields you can query on the Location entity. 
```
{
  location {
    description
    id
    site
    summary
    title
    object {
      id 
      summary
    }
  }
}
```
* For the nested queries you can use all the fields available for that entity. For simplicity we have limited this to `id` and `summary` for the docs.
#### Arguments
These are all the possible arguments for an location query:
```
page
size

id
summary
```

#### Sorting
The available sorting terms are:
```
id
summary
```
#### Aggregations
There are no aggregation terms for location.