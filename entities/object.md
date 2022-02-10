
### Object

#### Fields
These are the fields you can query on the object entity:

```
{
  object {
    classification
    collectionsOnlineId
    culture 
    date 
    department 
    description 
    exhibition
    identifier
    id
    inscription 
    legal 
    material 
    medium 
    measurements
    multimedia 
    name 
    note 
    period 
    provenance 
    status
    summary
    title

    agent {
        id
        summary
    }

    collector {
        id
        summary
    }

    maker {
        id
        summary
    }

    subject {
        id
        summary
    }

    tag {
        id
        summary
    }
  }
}

```
* For the nested queries you can use all the fields available for that entity. For simplicity we have limited this to `id` and `summary` for the docs.

#### Arguments
These are all the possible arguments for an object query:
```
page: int
size: int
sort: [{arg1: order}, {arg2: order}] 
aggregations: [field,field]

general: string

agentId: string
agent: string
collectionsOnlineId: string
culture: string
department : string
departmentId: string
displayed: boolean
dynasty: string
exhibition: string
exhibitionId: string
identifier: string
id: string
maker: string
makerId: string
material: string
name: string
period: string
provenance: string
reign: string
summary: string
subject: string
subjectId: string
title: string
year: YYYY
yearRange: {from:YYYY, to:YYYYY}
```

##### Sorting
Example sort by id:
```
{
  object(sort:[{id: "asc"}]){
       id
  }
}
```
The available sort terms are:
```
id
summary
year
```

#### Aggregations
You can create aggregations across different fields: 
```
{
object(aggregations:["department"]) {
     id    
  }
}
```
You can currently aggregate across these object fields:
```
classification
collector
culture
department
departmentID
maker
material
medium
period
place
provenance
subject
```