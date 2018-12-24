# Resources
here is a list of resources explained.

## ActivityTime
## Address

| title | type           | description            | example          |
| ----- | -------------- | ---------------------- | ---------------- |
| title | string         | address title          | my mother's home |
| lon   | decimal (8, 6) | geo longtitude decimal | 34.554934        |
| lat   | decimal (8, 6) | geo latitude decimal   | 43.234564        |
| plain | string         | plain address          | -                |
| city  | [City](#city)  | city of unit           | -                |

## Bid
## City

| title    | type                  | description                                                    | example   |
| -------- | --------------------- | -------------------------------------------------------------- | --------- |
| title    | string                | city title                                                     | vegas     |
| province | [Province](#province) | city's province, it's null if the parent object was a province | -         |
| lon      | decimal (8, 6)        | geo longtitude decimal                                         | 34.554934 |
| lat      | decimal (8, 6)        | geo latitude decimal                                           | 43.234564 |

## Demand
## Doctor

| title       | type                      | description                       | example                                |
| ----------- | ------------------------- | --------------------------------- | -------------------------------------- |
| first_name  | string                    | doctor's first name               | john                                   |
| last_name   | string                    | doctor's last name                | doe                                    |
| degree_id   | integer                   | id of degree                      | 32                                     |
| degree_str  | string                    | doctor's degree string            | -                                      |
| field_id    | integer                   | id of field                       | 32                                     |
| field_str   | string                    | doctor's field string             | -                                      |
| profile_url | url                       | doctor's profile picture http url | http://calcifer.ir/users/849438293.jpg |
| msc         | string                    | doctor's medical science code     | 438938                                 |
| gender      | [UserGender](#usergender) | user's gender code                | 2                                      |

## Nurse

| title       | type                      | description                       | example                                |
| ----------- | ------------------------- | --------------------------------- | -------------------------------------- |
| first_name  | string                    | nurse's first name               | john                                   |
| last_name   | string                    | nurse's last name                | doe                                    |
| degree_id   | integer                   | id of degree                      | 32                                     |
| degree_str  | string                    | nurse's degree string            | -                                      |
| field_id    | integer                   | id of field                       | 32                                     |
| field_str   | string                    | nurse's field string             | -                                      |
| profile_url | url                       | nurse's profile picture http url | http://calcifer.ir/users/849438293.jpg |
| msc         | string                    | nurse's medical science code     | 438938                                 |
| gender      | [UserGender](#usergender) | user's gender code                | 2                                      |

## Province

| title | type           | description            | example   |
| ----- | -------------- | ---------------------- | --------- |
| title | string         | province's title       | zanjan    |
| lon   | decimal (8, 6) | geo longtitude decimal | 34.554934 |
| lat   | decimal (8, 6) | geo latitude decimal   | 43.234564 |

## User

| title      | type                            | description                                       | example        |
| ---------- | ------------------------------- | ------------------------------------------------- | -------------- |
| username   | string                          | user's username                                   | mono           |
| email      | email address (string)          | if user didn't had email address then it's `NuLL` | email@site.com |
| phone      | phone string                    | user's phone that registered by.                  | 09215867485    |
| first_name | string                          | user's first name                                 | monoli         |
| last_name  | string                          | user's last name                                  | zay            |
| group_code | [UserGroupCode](#usergroupcode) | user's group code                                 | 3              |

### UserGroupCode

| value | description        |
| ----- | ------------------ |
| 1     | admin group user   |
| 2     | manager group user |
| 3     | doctor group user  |
| 4     | nurse group user   |
| 5     | patient group user |

### UserGender

| value | description |
| ----- | ----------- |
| 1     | male        |
| 2     | female      |

## Unit

| title      | type                            | description           | example     |
| ---------- | ------------------------------- | --------------------- | ----------- |
| title      | string                          | unit's title          | fargah      |
| mobile     | string                          | mobile phone number   | 09214875485 |
| telephone  | string                          | telephone number      | 01333485847 |
| address    | [UnitAddress](#unitaddress)     | unit's address object | -           |
| type       | [UnitType]                      | unit type             | 1           |
| group_code | [UnitGroupCode](#unitgroupcode) | unit's group code     | 3           |

### UnitAddress

| title | type           | description            | example   |
| ----- | -------------- | ---------------------- | --------- |
| lon   | decimal (8, 6) | geo longtitude decimal | 34.554934 |
| lat   | decimal (8, 6) | geo latitude decimal   | 43.234564 |
| plain | string         | plain address          | -         |
| city  | [City](#city)  | city of unit           | -         |

### UnitType

| value | description                                   |
| ----- | --------------------------------------------- |
| 1     | it's an actual unit. patients can go to place |
| 2     | it's a virtual unit. patients can't go there  |

### UnitGroupCode

| value | description |
| ----- | ----------- |
| 1     | hospital    |
| 2     | department  |
| 3     | poli-clinic |
| 4     | clinic      |
| 5     | labratory   |