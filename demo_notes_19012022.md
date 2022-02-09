# 19.01.2022 Demo notes
* We want to show you the new API first of all by doing some comparisons to examples on the collections page


## Searching for Objects

### Chairs: 
* chairs: 1138  vs 2135
* a general match with chair 
* beauty of graphql is we can cut down and find the specific information we want 
```
{
  object(general: "chair") {
    id
    summary
    identifier
    name
    title
    description
    medium
    legal
    creation
    department
    subject
    agent {
      id
      summary
    }
    classification
    inscription
    measurements
    provenance
    status
    datatype

  }
}

```
* So it will be easier if I cut down the response to just these fields
```
{
  object(general: "chair") {
    id
    summary
    identifier
  }
}
```
### Posters
* posters 3501 vs 5095
```
{
  object(general: "poster") {
    id
    summary
    identifier
    name
    title
    description
    medium
    legal
    creation
    department
    subject
    agent {
      id
      summary
    }
    classification
    inscription
    measurements
    provenance
    status
    datatype
  }
}
```

### Matchsafe
* matchsafes 4,067 vs 4213
* interesting point here I have added an aggregigation of the medium of the match safe
so we can learn more about the results
```
{
  object(general: "matchsafe" aggregations:["medium"]) {
    id
    summary
    identifier
    name
    title
    description
    medium
    legal
    creation
    department
    subject
    agent {
      id
      summary
    }
    classification
    inscription
    measurements
    provenance
    status
    datatype
  }
}

```

### Lamps
* you can also add more depth to the query by asking for specific periods

```
{
  object(general:"lamp" period:"art deco") {
    id
    summary
    name
    creation
    description
  }
}
```
## Searching for Agents

Dieter Rams:
```
{
  agent(name: "Dieter Rams") {
    id
    name
    nationality
    object {
      id
      summary
    }
  }
}
``` 

```
{
  agent(name: "Benjamin Dean Wyatt") {
    id
    name
    nationality
    object {
      id
      summary
    }
  }
}
```

```
{
  agent(name: "Robert") {
    id
    name
    nationality
    object {
      id
      summary
    }
  }
}
```