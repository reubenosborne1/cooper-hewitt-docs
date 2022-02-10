### Exhibition

#### Fields
These are all the fields you can query on the Exhibition entity. 
```
{
  exhibition {
    category
    collectionsOnlineId
    id
    identifier
    label
    location
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
These are all the possible arguments for an department query:
```
page: int
size: int
sort: [{arg1: order}, {arg2: order}] 

general: string

category: string
collectionsOnlineId: string
id: string
identifier: string
label: string
location: string
locationId: string
summary: string
```

#### Sorting
The available sorting terms are:
```
id
summary
```
#### Aggregations
You can create aggregations across different fields: 
```
{
exhibition(aggregations:["label"]) {
     id    
  }
}
```
You can currently aggregate across these exhibition fields:
```
label
location
locationId
```