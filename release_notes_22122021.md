# 22.12.2021: Release Notes

* Tags are still not available

## New Entities 

-  Classification

```
{
  classification {
    id
    datatype
    summary
  }
}
```

- Department

```
{
  department {
    id
    datatype
    summary
  }
}
```

- Event

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
- Location

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

- Package 

```
{
  package {
    id
    datatype
    name
    summary
  }
}
```

- Term 

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


## New Object fields
```
{
  object {
  	catalogued
  	subject
  	provenance
  	material
  }
}
```

*** Subject output needs to be reworked in ElasticSearch

## New object search points

You can now search using 
```
provenance
material
subject
subjectId
agent 
```

```
{
  object(subject: "Medici Family") {
    id
    summary
  }
}
```

Above returns objects where the subject of the object is the Medici Family.
```
{
  object(agent:"IBM") {
    id
    summary
  }
}

```
Or above searches against all agent roles for IBM 


## New search points on nested queries

```
{
  agent (name:"Zack Peabody"){
    id
    summary
    object(relationship:"maker") {
      id
    }
  }
}

```

Now you can ask for object assoicted to each agent record, but only where the relationship between the two is 'maker' or 'subject'. 
The objects in the reponse were made by Zak Peabody:
```
{
  "data": {
    "agent": [
      {
        "id": "agent-306",
        "summary": {
          "title": "Zack Peabody"
        },
        "object": [
          {
            "id": "object-199539"
          },
          {
            "id": "object-196417"
          },
          {
            "id": "object-196416"
          }
        ]
      }
    ]
  },
  "extensions": {
    "pagination": {
      "hits": 1,
      "per_page": 10,
      "current_page": 0,
      "number_of_pages": 1
    }
  }
}
```

