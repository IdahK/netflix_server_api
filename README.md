Consuming the api
======

## Register subscribers
URL :  /subscribers

Method : post

Body

```json
{
    "name": "Jane Doe",
    "identificationNumber": "54321"
}
```
Responses
  1. If a new user
```text
    {
        Subscriber:54321 saved
    }
```

  2.. If user is already registered 
```text
    {
        Subscriber:5233 already registered.Cannot register again
    
    }
```
## View categories

URL :  /categories

Method : get

Response

```json
[
    {
        "id": 1,
        "categoryName": "Comedy"
    },
    {
        "id": 2,
        "categoryName": "Animation"
    },
    {
        "id": 3,
        "categoryName": "Drama"
    },
    {
        "id": 4,
        "categoryName": "Action"
    }
]
```
## Movies

   ###  Search movies 

URL :  /movies

Method : get

Response

```json
    [
        {
            "id": 5,
            "name": "Lego",
            "type": "original",
            "yearOfRelease": "2018",
            "contentowner": null,
            "categories": [
                {
                    "id": 2,
                    "categoryName": "Animation"
                }
            ]
        },
        {
            "id": 6,
            "name": "Avengers Endgame",
            "type": "original",
            "yearOfRelease": "201",
            "contentowner": null,
            "categories": [
                {
                    "id": 4,
                    "categoryName": "Action"
                }
            ]
        }
    ]
```

###  Search movies by Category and Type

URL: /movies/{categoryId}

METHOD: GET

Request Parameter: type= <suggested/original>

```json
{
 "type": "original"
}
```

Response
```json
[
    {
        "id": 5,
        "name": "Lego",
        "type": "original",
        "yearOfRelease": "2018",
        "contentowner": null,
        "categories": [
            {
                "id": 2,
                "categoryName": "Animation"
            }
        ]
    },
    {
        "id": 6,
        "name": "Avengers Endgame",
        "type": "original",
        "yearOfRelease": "201",
        "contentowner": null,
        "categories": [
            {
                "id": 4,
                "categoryName": "Action"
            }
        ]
    }
]
```

###  Suggest/add movies for subscribers
URL: /movies

METHOD: POST

Request Header: "identificationNumber"

Body

```json
{
   "name": "Joker",
   "yearReleased": "2020",
   "categories": [
         {
           "categoryName": "comedy"
         },
         {
           "categoryName": "action"
         }
   ]
 }
```

Response
```json
{
    "id": 13,
    "name": "Joker",
    "type": "suggested",
    "yearOfRelease": null,
    "contentowner": {
        "id": 7,
        "identificationNumber": "5233",
        "fullname": "Idah Koome"
    },
    "categories": [
        {
            "id": 11,
            "categoryName": "comedy"
        },
        {
            "id": 12,
            "categoryName": "action"
        }
    ]
}
```



 



   

 