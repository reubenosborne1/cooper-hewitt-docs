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
- [What Objects did Dieter Rams make between X and Y?](/examples/example1.md)
- [What Objects were X a Subject of? ](/examples/example2.md)
- [What exhibitions have been in venue X and what objects were exhibited?](/examples/example3.md)
- [Get me a X X from X, which was made from X. ](/examples/example4.md):
- [Example 5](/examples/example5.md):

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