### Department

#### Fields
These are all the fields you can query on the Department entity. 
```
{
  department {
    collectionsOnlineId
    id
    identifier
    summary
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

collectionsOnlineId:string
id: string
summary: string
```

#### Sorting
The available sorting terms are:
```
id
summary
```
#### Aggregations
There are no aggregation terms for department.