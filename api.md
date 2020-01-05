### API 

Some examples of how users can access your API so that they can get predictions
```
url = 'http://127.0.0.1:5000/'
params ={'query': 'that movie was boring'}
response = requests.get(url, params)
response.json()
```
{
    "prediction": "Negative",
    "confidence": 0.128
}

```
$ curl -X GET http://127.0.0.1:5000/ -d query='that movie was boring'
```
{
    "prediction": "Negative",
    "confidence": 0.128
}

```
$ http http://127.0.0.1:5000/ query=='that movie was boring'
```
HTTP/1.0 200 OK 
Content-Length: 58  
Content-Type: application/json 
Date: Fri, 31 Aug 2018 18:49:25 GMT 
Server: Werkzeug/0.14.1 Python/3.6.3 
{
    "prediction": "Negative",
    "confidence": 0.128
}


- Rest API
  ```
  API is about what is going to be done, not about how
  Naming of API must convey "what" and only do that. (no side-effects)
  Specific error message should be returned
  API is a developer UI, ensure UX is pleasant
  Keep only two baseurls per resource
  Keep verbs out of baseurls, (as HTTP verbs do that). Use noun for resources
  GET /tickets
  GET /tickets/123
  Use plural url formats, e.g. tickets (not ticket)      
  Always use SSL
  Good documentation (should be publicly easily available)
  Always version APIs
  Create aliases for common queries
  API should have ability to take json as input
  Limit which fields are returned by API
  RESTful APIs should be stateless. And the authentication should not depend on cookies or sessions.
  ```
