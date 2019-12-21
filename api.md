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
