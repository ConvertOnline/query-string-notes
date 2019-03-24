
A missing specification of the HTTP protocol is how to pass arrays in a query string. Since there is no specific standard, programming languages and framework have defined they own implementation. This article covers the 3 popular way of passing arrays in a query string and for each a list of frameworks and languages that support them.

## Multiple assignements
A common method to pass an array via query string is by assigning multiples values to the same key.
```http
HTTP GET http://somesite.com?categoryids=1&categoryids=2&categoryids=3
```

## Multiple array assignements
A common method to pass an array via query string is by assigning multiples values to the same key with openning and closing square bracket as a suffix.
```http
HTTP GET http://somesite.com?categoryids[]=1&categoryids[]=2&categoryids[]=3
```

## Multiple array assignements with index
A common method to pass an array via query string is by assigning multiples values to the same key with openning square bracket, index and closing square bracket as a suffix.
```http
HTTP GET http://somesite.com?categoryids[0]=1&categoryids[1]=2&categoryids[2]=3
```
Why would you want to define indexes? Index would help to add more complex data. For example the request below 
```http
HTTP GET http://somesite.com?filters[0][count]=1&filters[0][name]=2
```
can be converted to the JSON
```json
{"filters": [{"count": 1, "name": 2}]}
```

Language | Framwork     | key=value         |key[]=value|key[index]=value
| ----------| ---------- | ---------- | ---------- |---------- |
|Javascript| Jquery       | With `traditional: true` flag when calling $.ajax or $.get       | Default| 
|Javascript| Angular  1     | Default behaviour       |With a work around. Add `[]` as prefix to key  | 
