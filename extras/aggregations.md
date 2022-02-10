
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