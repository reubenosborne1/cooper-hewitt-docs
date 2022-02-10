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