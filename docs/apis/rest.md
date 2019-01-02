# Rest APIs

here is the complete list of APIs with their details

#### Send Token

this api sends a new token to client's phone

> `POST` /api/auth/send-token

> middleware: -

| title      | type                                          | description                   | example     |
| ---------- | --------------------------------------------- | ----------------------------- | ----------- |
| phone      | string, phone number                          | string in phone number format | 09214837485 |
| group_code | [UserGroupCode](/api/resources#usergroupcode) | user group code               |

in case of success the result would be:

```
{
    "message": "token sent to phnoe number"
}
```

#### Verify

this api verifies the code sent to phone number

> `POST` /api/auth/verify-token

> middleware: -

| title | type   | description      | example |
| ----- | ------ | ---------------- | ------- |
| token | string | string, 6 digits | 485748  |

in case of success if user was regsitered before:

```
{
    "registered": true,
    "access_token":  [TOKEN_STRING],
    "expires_at":   [TIMESTAMP],
    "user":         [User Model]
}
```

in case of success if user was not registered before:

```
{
    "registered": false,
    "access_token":  [TOKEN_STRING],
    "expires_at":   [TIMESTAMP],
}
```


#### Get Profile

> `GET` /api/auth/profile

> middleware: `auth`

output would be [User](apis/resources/#user)

#### Edit Profile

> `POST` /api/auth/profile

> middleware: `auth`

this api edits the user information by user itself

##### parameters

| title      | type          | description              | example           |
| ---------- | ------------- | ------------------------ | ----------------- |
| first_name | string        | user's first name        | john              |
| last_name  | string        | user's last name         | doe               |
| email      | email(string) | users' email             | johndoe@gmail.com |
| slug       | string        | unique slug for username | johnyyy           |


if user was a doctor the response object would have these fields too:

| title       | type              | description                         | example                                                     |
| ----------- | ----------------- | ----------------------------------- | ----------------------------------------------------------- |
| msc         | string            | medical science code                | 485784                                                      |
| fields      | [[Field](#field)] | doctor's fields                     | []                                                          |
| start_year  | integer           | the starting medical year of doctor | 1390                                                        |
| profile_url | http url          | doctor's profile url                | http://doctorsoal.com/users/489hcinccn4928cuocbxon23h98.png |
| gender      | [Gender](#gender) | user's gender                       | 2                                                           |

if user was a patient then response would have these fields too:

| title       | type              | description                            | example                                                     |
| ----------- | ----------------- | -------------------------------------- | ----------------------------------------------------------- |
| gender      | [Gender](#gender) | user's gender                          | 2                                                           |
| id_number   | string            | id number of user                      | 4738483748                                                  |
| birth_date  | string            | user's birth date in format yyyy-mm-dd | 1373-04-22                                                  |
| profile_url | http url          | doctor's profile url                   | http://doctorsoal.com/users/489hcinccn4928cuocbxon23h98.png |

#### Logout

> `POST` /api/auth/logout

> middleware: `auth`

#### Search

> `GET` /api/search

> middleware: -

#### Get Unit

> `GET` /api/unit/[unit-slug]

> middleware: -

#### Get Doctor

> `GET` /api/doctor/[doctor-slug]

> middleware: -

#### Create Visit Demand

this api creates a visit demand for patient.

> `GET` /api/demands/create/visit

> middleware: `auth`

parameters are:

| title         | type         | description                                       | example                                |
| ------------- | ------------ | ------------------------------------------------- | -------------------------------------- |
| activity_time | uuid4 string | activity_time of unit_user                        | 4874-vb384-48398vsckjbh239-vhvu4-vvjb4 |
| day           | timestamp    | timestamp of the visit day in 00:00               | 157467632                              |
| description   | string       | optinal description about the visit time. max:200 | some informations                      |

is case of success the response would be:

```
{
    "id": UUID_OF_VISIT_TIME,
    "date": TIMESTAMP_WHEN_PATIENT_HAVE_TO_BE_IN_UNIT,
}
```

if patient profile wasn't complete then response would be:

```
[
    {
        "code" : "profileIncomplete"
        "field": "profile",
        "message": "client's profile is incomplete."
    }
]
```