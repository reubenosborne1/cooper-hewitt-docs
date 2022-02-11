This query returns agents who are French and have made an Object. However, the Objects returned aren't necessarily the ones they have made. They are just associated OBjects. 
```
{
  agent(nationality: "French", relationship:"maker") {
    id
    summary
    object {
      id
      summary
    }
  }
}

```

This is the same query however we are specifically requesting for objects they have made.
```
{
  agent(nationality: "French", relationship:"maker") {
    id
    summary
    object (relationship:"maker") {
      id
      summary
    }
  }
}

```