# API - GraphQL Query Documentation with examples

## Quick links:
### Entities: 

- [Agent](https://github.com/reubenosborne1/cooper-hewitt-docs/blob/master/demo_notes_19012022.md)
- [Classification](#classificaion)
- [Department](#department)
- [Event](#event)
- [Location](#location)
- [Object](#object)
- [Package](#package)
- [Tag](#tag)
- [Term](#term)


### Extras:
- [Nested Queries](#nested-queries)
- [Aggregations](#aggregations)
- [Pagination](#pagination)
- [Fragments](#fragments)
- [Error Handling](#error-handling)

## Introduction
GraphQL queries follow this basic structure:
```
{
  object (arguments) {
    fields
  }
}
```
The resultant data follows the same structure as the query
```
{
  "data": {
    "object": {
      "field": value
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
### Classification

#### Fields
These are all the fieds you can query on the Classification entity. 
```
{
  classification {
    id
    datatype
    summary
  }
}
```
#### Arguments
These are all the possible arguments for an Classification query:
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
There are no aggregation terms for department.

### Department

#### Fields
These are all the fieds you can query on the Department entity. 
```
{
  department {
    id
    datatype
    summary
  }
}
```
#### Arguments
These are all the possible arguments for an department query:
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
There are no aggregation terms for department.

### Event

#### Fields
These are all the fieds you can query on the Event entity. 
```
{
  event {
    id
    datatype
    date
    department
    description
    location
    name
    summary
  }
}

```
#### Arguments
These are all the possible arguments for an Event query:
```
page
size

aggregations

id
summary
department
departmentId
location
locationId
```

#### Sorting
The available sorting terms are:
```
id
summary
```
#### Aggregations
You can currently aggregate across these Event fields:
```
department
departmentId
location
locationId
```


### Location

#### Fields
These are all the fieds you can query on the Location entity. 
```
{
  location {
    id
    datatype
    description
    summary
    title
  }
}
```
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
### Package

#### Fields
These are all the fieds you can query on the Package entity. 
```
{
  department {
    id
    datatype
    summary
  }
}
```
#### Arguments
These are all the possible arguments for an Package query:
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
There are no aggregation terms for Package.

### Tag

#### Fields
These are all the fieds you can query on the Tag entity. 
```
{
  tag {
    id
    datatype
    summary
  }
}
```
#### Arguments
These are all the possible arguments for an Tag query:
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
There are no aggregation terms for Tag.

### Term

#### Fields
These are all the fieds you can query on the Term entity. 
```
{
  term {
    id
    datatype
    hierarchy
    parent
    summary
    term
    thesaurus
  }
}
```
#### Arguments
These are all the possible arguments for an Term query:
```
page
size

aggregations

id
summary
thesaurus
```

#### Sorting
The available sorting terms are:
```
id
summary
```
#### Aggregations
You can currently aggregate across these Term fields:
```
thesaurus
```



## Nested Queries
Nested queries allow you to query entities that are linked, for example the agents associated with an object record. This also allows you to specify the fields you want for both entities. The nested queries also allow arguments to be passed, but this will be in a reduced format.
### object.agent
Find agents linked to an object.
```
{
  object {
    id
    agent {
      id
      name
    }
  }
}
```
#### Nested Arguments
```
size
page
``` 

### agent.object
Return agents matching this name and the objects they are linked with, specifically where they are the 'maker'.
```
{
  agent(name: "Frank Lloyd Wright") {
    id
    object (relationship: "maker"){
      id
      summary
    }
  }
}

```
### Nested Arguments
```
size
page
relationship
```
** Note relationship only has the allowed values "maker" and "subject" to match the object schema.

## Aggregations
The aggregation data can be found in the response's extension block. Here is an example response for aggregating on an object.departments, it names the aggregation after the field you have used and offers the top 10 results.
```
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
          {
            "key": "Textiles Department",
            "doc_count": 26275
          },
          {
            "key": "Wallcoverings Department",
            "doc_count": 9189
          },
          {
            "key": "Exhibitions Department",
            "doc_count": 2480
          },
          {
            "key": "Archives Department",
            "doc_count": 800
          },
          {
            "key": "Smithsonian Libraries",
            "doc_count": 183
          },
          {
            "key": "Digital",
            "doc_count": 19
          },
          {
            "key": "Registrars Office",
            "doc_count": 1
          },
          {
            "key": "Training",
            "doc_count": 1
          }
        ]
      }
    },
```
You can do multiple aggregations:
```
{
  object(aggregations: ["department", "maker"]) {
    id
  }
}
```

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

## Fragments 

GraphQL offers reusable units called fragments, they let you construct a set of fields to include in queries where you need to. Below we have the example 'briefObjectFields, where we return a subset of the possible object fields required for this query.
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
- Attemping to use an aggregation term that is not accepted.
```
{
      "message": "errortest is not a valid key! Please use these keys: ['classification', 'culture', 'datatype', 'department', 'departmentId', 'maker', 'material', 'period', 'place']"
}
```