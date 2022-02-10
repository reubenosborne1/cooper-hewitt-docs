# API - GraphQL Query Documentation with examples

## Quick links:
### Entities: 

- [Agent](/entities/agent.md)
- [Department](/entities/department.md)
- [Exhibition](/entities/exhibition.md)
- [Location](/entities/location.md)
- [Object](/entities/object.md)
- [Package](/entities/package.md)
- [Tag](/entities/tag.md)
- [Term](/entities/term.md)

### Extras:
- [Aggregations](/extras/aggregations)
- [Pagination](/extras/pagination)
- [Fragments](/extras/fragments)
- [Error Handling](/extras/error_handling)

### Examples:
- [All objects made by Dieter Rams](/examples/example1.md)
- [All agents who makers](/examples/example2.md)
- [What objects were at this exhibition?](/examples/example3.md)
- [Example 4](/examples/example4.md):

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