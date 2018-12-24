# APIs
calcifer engine implements several apis to use it completely from outside. apis helps to outsource the project and just use the backend part. APIs are based on REST and JSON tech. there are some common rules between all apis in calcifer.

## Requests

requests have different parts: `verb`, `endpoint` and `parameters`.

### verbs

| verb   | description                                                                |
| ------ | -------------------------------------------------------------------------- |
| GET    | to retrive items or other informations. non-action                         |
| POST   | to do an action. this verb doesn't create any entity in database by itself |
| PUT    | create and update and actual entity in database                            |
| DELETE | delete an entity from database                                             |

### endpoints

endpoints completely explained in [REST APIs](/apis/rest).

### parameters

you are free to send your parameters in `json` or `form-encoded` or `www-urlencoded`. but consider that you can upload files just when you are using `form data` inputs.

## Responses

responses have two parts: `content` and `http response code`.

### HTTP Response Code

every different http code means something:

| HTTP code | description                                                       |
| --------- | ----------------------------------------------------------------- |
| 200       | request was successfull                                           |
| 400       | bad request. some errors in validation of inputs                  |
| 401       | client is unauthorized                                            |
| 402       | client doesn't have enough credits                                |
| 403       | client doesn't have access to entity                              |
| 404       | requested entity not found                                        |
| 405       | requested endpoint had different verb. used wrong verb in request |
| 419       | client is spaming the service                                     |
| 500       | server internal error                                             |

### Content

contents are in json format. but the structure is different for each http response code:

#### 200

content of this http code doesn't have any structure.

#### 400

content of this http code is the validation errors that happened. here is the structure:

```
[
    {
        "code" : STRING,
        "field": STRING,
        "message": STRING
    },
]
```

code is a unique merge of field and the unvalid rule. field is title of input that is invalid. message is a human readable string explaining the error.

#### 401

content would be:

```
{
    "message": "client is unauthorized."
}
```

#### 402

content would be:

```
{
    "message": "client doesn't have enough credit"
}
```

#### 403

content would be:

```
{
    "message": "client doesn't have access to the requested entity"
}
```

#### 404

content would be:

```
{
    "message": "requested entity not found"
}
```

#### 405

content would be:

```
{
    "message": "wrong request. wrong verb"
}
```

#### 419

content would be:

```
{
    "message": "client is banned from service due the number of requested"
}
```

#### 500

content would be:

```
{
    "message": "server internal error."
}
```