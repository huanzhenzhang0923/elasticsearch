## Define Mapping


PUT /hotel_apps
{
  "mappings": {
      "properties": {
        "hotels": {
            "properties": {
                "pin": {
                    "properties": {
                        "location": {
                            "type": "geo_point"
                        }
                    }
                }
            }
        }
      }
  }
}

## Index Data

POST /hotel_apps/_doc/1
{
    "hotels":{
      "name": "喜来登大酒店",
      "pin" : {
          "location" : {
              "lat" : 40.15,
              "lon" : -71.36
          }
      }
    }
}


GET /hotel_apps/_search

## Distance Search

GET /hotel_apps/_search
{
  "query": {
    "geo_distance": {
        "distance": "200km",
        "hotels.pin.location": {
          "lat": 40,
          "lon": -70
        }
    }
  }
}

## Bonding Box Search


GET /hotel_apps/_search
{
  "query": {
    "geo_bounding_box": {
      "hotels.pin.location": {
        "top_left" : {
            "lat" : 40.73,
            "lon" : -74.1
        },
        "bottom_right" : {
            "lat" : 40.01,
            "lon" : -71
        }
      }
    }
  }
}