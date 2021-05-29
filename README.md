# Coffee Shop
This project shows knowledge how to connect the application to a third party autentication service. In this case Auth0.

The app itself:

1. Display graphics representing the ratios of ingredients in each drink.
2. Allow public users to view drink names and graphics.
3. Allow the shop baristas to see the recipe information.
4. Allow the shop managers to create new drinks and edit existing drinks.

## Pre-requisites
In order to work with the project, you need to have the following installed on your computer:

Python 3.7
Postgresql
Node.js
Node Package Manager (NPM)

## Setup
Please follow instructions in readmes for each part of the app inside each folder

1. [`./backend/`](./backend/README.md)
2. [`./frontend/`](./frontend/README.md)

### Quick setup for frontend
Open a terminal, cd into the folder and run:
```
npm i
ionic serve
```
Frontend runs on `port:8100`

### Quick setup for backend
Open another terminal, cd into `backend/srd` and run:
```
py -3.7 -m venv venv
venv\Scripts\activate 
pip install -r requirements.txt
set FLASK_APP=api.py
flask run --reload
```
Backend runs on `port:5000`


# API Reference
This app can only be run locally and it is not hosted as base URL. It is hosted by default `http://127.0.0.1:5000/`.

## Error Handling
Errors are returned as JSON object in this format:
```
{
      "success": False, 
      "error": 400,
      "message": "Bad request"
}
```
The API can return errors when the request fails:
* 500: Internal Server Error
* 404: Not Found
* 409: Already Exists
* 422: Unprocassable
* 403: Permission not found.
* 401:
    * Authorization header is expected.
    * Token not found.
    * Authorization header must start with "Bearer".
    * Authorization malformed.
    * Token expired.
    * Incorrect claims. Check audience and issuer.
* 400:
    * Permissions not included in JWT.
    * Unable to parse authentication token.
    * Unable to find the appropriate key.

## Endpoints
### GET /drinks
This endpoint is public.
Returns `drinks` array of `drink` objects in short description of recipe.
*Sample return*
```
{
    "drinks": [
        {
            "id": 1,
            "recipe": [
                {
                    "color": "blue",
                    "parts": 1
                }
            ],
            "title": "water"
        }
    ],
    "success": true
}
```

### GET /drinks-detail
This enpoint requires "get:drinks-detail" permission.
Returns `drinks` array of `drink` objects. In this case you get the name of parts included inside.
*Sample return*
```
{
    "drinks": [
        {
            "id": 1,
            "recipe": [
                {
                    "color": "blue",
                    "name": "water",
                    "parts": 1
                }
            ],
            "title": "water"
        }
    ],
    "success": true
}
```

### POST /drinks
This endpoint requires "post:drinks" permission.
It recieves a JSON body containing title and recipe array.
Returns a newly created drink.
*JSON object sent to API*
{
    "title": "Sample",
    "recipe": [{
        "name": "Sample",
        "color": "blue",
        "parts": 1
    }]
}
*Sample return*
{
    "drinks": [
        {
            "recipe": [
                {
                    "color": "blue",
                    "name": "Sample",
                    "parts": 1
                }
            ],
            "title": "Sample"
        }
    ],
    "success": true
}

### PATCH /drinks/{drink_id}
This endpoint requires "patch:drinks" permission.
Recieves JSON object for the changes that are entered.
Returns drinks array containing the updated drink.
*JSON object sent to API*
{
    "title": "Patch"
}
*Sample return*
{
    "drinks": [
        {
            "recipe": "[{\"name\": \"water\", \"color\": \"blue\", \"parts\": 1}]",
            "title": "Patch"
        }
    ],
    "success": true
}

### DELETE /drinks/{drink_id}
This endpoint requires "delete:drinks" permission.
This endpoit deletes the drink provided in the endpoint.
Returns an object containing the ID of the deleted drink.
*Sample return*
```
{
    "delete": 2,
    "success": true
}
```
## Authors
- API and Authorization by Jaka Presecnik
- Starter code with frontend provided from Udacity [link](https://github.com/udacity/FSND/tree/master/projects/03_coffee_shop_full_stack/starter_code)