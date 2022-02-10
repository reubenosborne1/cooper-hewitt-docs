
### Object

#### Fields
These are the fields you can query on the object entity:

```
{
  object {
    id
    classification
    creation
    datatype
    department
    description
    identifier
    inscription
    legal
    material
    measurements
    medium
    name
    note
    provenance
    status
    subject
    summary
    title
    agent {
      id
    }
    tag {
      id
    }
  }
}

```

#### Arguments
These are all the possible arguments for an object query:
```
page: int
size: int
sort: [{arg1: order}, {arg2: order}] 
aggregations: [field,field]

_general: string

agentId: string
agent: string
creationYear: {from:YYYY, to:YYYYY}
culture: string
datatype: string
department : string
departmentId: string
dynasty: string
identifier: string
id: string
maker: string
makerId: string
material: string
period: string
provenance: string
reign: string
summary: string
subject: string
subjectId: string
title: string


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
The avaialable sort terms are:
```
id
summary
creationYear
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
culture
datatype
department
departmentID
maker
material
period
place
provenance
```