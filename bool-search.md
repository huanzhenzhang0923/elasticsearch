## Add Bool Search must, must not, should
GET /recipe/_search
{
  "query": {
    "bool": {
      "must": [
        {
          "match": {
            "ingredients.name": "parmesan"
          }
        }
      ]
      , "must_not": [
        {
          "match": {
            "ingredients.name": "tuna"
          }
        }
      ]
      , "filter": {
        "range": {
            "preparation_time_minutes": {
              "lte": 15
            }
          }
      }
    }
  }
}