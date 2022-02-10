### Agent

#### Fields
These are the fields you can query on the agent entity:

```
{
  agent {
    birth
    classification
    collectionsOnlineId
    death
    description
    dissolved
    founded
    id
    identifier
    name
    nationality
    role
    summary
    vocation
    object {
      id
      summary
    }
  }
}
```

#### Arguments
These are all the possible arguments for an agent query:
```
page: int
size: int
sort: [{arg1: order}, {arg2: order}] 
aggregations: [field,field]

general: string

collectionsOnlineId: string
date: YYYY
dateRange: {from:YYYY, to:YYYY}
description: string
identifier: string
id: string
name: string
nationality: string
summary: string
relationship: string
vocation: string
```

##### Sorting
Example sort by id:
```
{
  agent(sort:[{id: "asc"}]){
       id
  }
}
```
Then sortable terms are:
```
birth
death
forename
surname
id
name

```

#### Aggregations
You can create aggregations across different fields: 
```
{
  agent(aggregations:["relationship"]) {
     id    
  }
}
```
You can currently aggregate across these object fields:
```
nationality
relationship
vocation
```