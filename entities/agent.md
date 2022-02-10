### Agent

#### Fields
These are the fields you can query on the agent entity:

```
{
  agent {
    id
    birth
    classification
    datatype
    death
    defunct
    description
    founded
    identifier
    name
    nationality
    summary
    vocation
    object {
      id
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

_general: string

date: {from:YYYY, to:YYYYY}

datatype: string
description: string
identifier: string
id: string
name: string
nationality: string
summary: string
role: string
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
id
firstName
lastName
```
loans
#### Aggregations
You can create aggregations across different fields: 
```
{
  agent(aggregations:["role"]) {
     id    
  }
}
```
You can currently aggregate across these object fields:
```
datatype
nationality
role
vocation
```