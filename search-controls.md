## Average And Sort
```
GET /recipe/_search
{
  "_source": ["title","ratings"], 
  "query": {
    "match_all": {}
  },
  "sort":[
    {
      "ratings": {
        "order":"desc",
        "mode": "avg"
      }
    }
  ]
}
```


## Control Size

```
GET /recipe/_search?size=2
{
  "_source": "title", 
  "query": {
    "match": {
      "title": "pasta"
    }
  }
}

```

```
GET /recipe/_search?size=2
{
  "query": {
    "bool": {
      "must": [
        {
          "match": {
            "title": "pasta"
          }
        }
      ],
      "filter": {
        "range": {
          "preparation_time_minutes": {
            "gte": "15"
          }
        }
      }
    }
  }
}
```