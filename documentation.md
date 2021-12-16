# API - GraphQL Query Documentation with examples

## Quick links:
- [Object](#object)
- [Agent](#agent)
- [Pagination](#pagination)
- [Fragments](#fragments)
## Introduction
GraphQL queries follow this basic structure:
```
{
  object (arguments) {
    fields
  }
}
```
The resultant data follows the same structure as the query:
```
{
  “data”: {
    “object”: {
      “field”: value
    }
  }
}
```
There is also an extensions block in addition to the data response. This follows the GraphQL specifications and allows us to write more detailed responses, including information regarding pagination and aggregations.

```
  "extensions": {
    "aggregations": {
      "department": {
        "doc_count_error_upper_bound": 0,
        "sum_other_doc_count": 0,
        "buckets": [
          {
            "key": "Drawings, Prints, and Graphic Design Department",
            "doc_count": 129079
          },
          {
            "key": "Product Design and Decorative Arts Department",
            "doc_count": 28924
          },
          ...
        ]
      }
    },
    "pagination": {
      "hits": 196951,
      "per_page": 10,
      "current_page": 0,
      "number_of_pages": 19696
    }
  }
```

## Breakdown of the Different Entities

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
    measurements
    medium
    name
    note
    status
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

creationYear: {from:YYYY, to:YYYYY}
culture: string
datatype: string
department : string
departmentID: string
dynasty: string
identifier: string
id: string
maker: string
period: string
reign: string
summary: string
title: string
```
##### Sorting
Example sort by id:
```
{
  object(sort:[{id: “asc”}]){
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
```

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
    role
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
  agent(sort:[{id: “asc”}]){
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

## Pagination

We are using ES’ built in pagination where the user can set per query the size and the page of the result list.  
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

## Fragments 

GraphQL offers reusable units called fragments, they let you construct a set of fields to include in queries where you need to. Below we have the example ‘briefObjectFields, where we return a subset of the possible object fields required for this query.
```
{
  object_193341: object (id:"object-193341"){
    ...briefObjectFields
  },
  object_274301: object (id:"object-274301"){
    ...briefObjectFields
  }
}
```
```
fragment briefObjectFields on Object{
  id
  identifier
  description
  creation
  department
  summary
```