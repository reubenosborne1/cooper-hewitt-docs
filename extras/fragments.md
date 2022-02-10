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
