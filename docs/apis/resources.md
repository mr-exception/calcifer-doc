# Resources
here is a list of resources. resource models are the objects returned from api request in json format.

## Bid:Visit

this kind of bid is for clinics. they don't have any deposit and all the money is paid offline.

| title       | type                   | description                    | example                |
| ----------- | ---------------------- | ------------------------------ | ---------------------- |
| clinic      | [Clinic](#clinic)      | clinic that reserved the visit | -                      |
| date        | timestamps             | timestamp of visit time        | 1548574857             |
| description | string                 | description of bid             | please be there ontime |
| status      | [BidStatus](#bistatus) | status of bid                  | 2                      |

### BidStatus

status enum of bids

| value | description                                            |
| ----- | ------------------------------------------------------ |
| 1     | pending, just created by unit                          |
| 2     | accepted by patient. waiting for unit and doctor/nurse |
| 3     | accepted by unit                                       |
| 4     | accepted by doctor/nurse                               |
| 5     | patient refused the bid                                |
| 6     | unit refused the bid                                   |
| 7     | doctor/nurse refused the bid                           |
| 8     | accepted by all                                        |
| 9     | refused by all                                         |
| 10    | bid is done                                            |
| 11    | bid is canceled                                        |
| 12    | bid is accepted all is paid                            |

## City

city is an object that defines the geo informations of a city

| title    | type                  | description                                                                               | example   |
| -------- | --------------------- | ----------------------------------------------------------------------------------------- | --------- |
| title    | string                | title of city                                                                             | paris     |
| lon      | decimal(8, 6)         | longtitude of city geo                                                                    | 34.584758 |
| lat      | decimal(8, 6)         | latitude of city geo                                                                      | 42.384748 |
| province | [Province](#province) | the province object that contains the city. it's null when the parent model is a province | -         |

## Clinic

clinic is a kind of unit that contains only a single doctor/nurse and a several secretaries. here is the fields:

| title        | type              | description                                          | example         |
| ------------ | ----------------- | ---------------------------------------------------- | --------------- |
| title        | string            | clinic title                                         | green house     |
| city         | [City](#city)     | city of clinic                                       | -               |
| doctor       | [Doctor](#doctor) | doctor of clinic                                     | -               |
| address_text | string            | address in plain text                                | st north. n 245 |
| lon          | decimal(8, 6)     | longtitude of clinic geo                             | 34.584758       |
| lat          | decimal(8, 6)     | latitude of clinic geo                               | 42.384748       |
| phone        | string            | phone number                                         | 021483748       |
| mobile       | string            | mobile number. usually the secretary's mobile number | 092148574857    |
| slug         | string            | unique string to define the page of clinic           | greenee         |

## Doctor

doctor is group of users registered by doctor permission. client can search them in project. here is the fields:

| title       | type     | description                   | example                                        |
| ----------- | -------- | ----------------------------- | ---------------------------------------------- |
| first_name  | string   | first name of doctor          | johan                                          |
| last_name   | string   | last name of doctor           | doe                                            |
| start_year  | integer  | the starting year of activity | 1383                                           |
| profile_url | http url | the http url of profile       | http://doctorsoal.com/users/47483dhxcbh2j.jpeg |
| msc         | string   | the msc of doctor             | 4837475                                        |
| fields      | [Field]  | fields of doctor              | []                                             |

## Entry
## Field

fields are the working area of doctors. they're like tags. here are the descriptions:

| title | type   | description           | example                     |
| ----- | ------ | --------------------- | --------------------------- |
| title | string | title of field        | orthopedic                  |
| id    | uuid   | uuid v4 unique string | 4837-4854-584758478573-4958 |

## OrthopedicClinic

an Orthopedic clinic is that kind of unit contains only orthopedic doctors/nurses. here is the fields:

| title        | type          | description                                          | example                                        |
| ------------ | ------------- | ---------------------------------------------------- | ---------------------------------------------- |
| title        | string        | clinic title                                         | green house                                    |
| city         | [City](#city) | city of clinic                                       | -                                              |
| address_text | string        | address in plain text                                | st north. n 245                                |
| lon          | decimal(8, 6) | longtitude of clinic geo                             | 34.584758                                      |
| lat          | decimal(8, 6) | latitude of clinic geo                               | 42.384748                                      |
| phone        | string        | phone number                                         | 021483748                                      |
| mobile       | string        | mobile number. usually the secretary's mobile number | 092148574857                                   |
| slug         | string        | unique string to define the page of clinic           | greenee                                        |
| logo_url     | http url      | clinic logo url                                      | http://doctorsoal.com/units/84847273287384.png |

## User

use is a base object extended on group and permissions. here is a complete description of fields:

| title      | type   | description          | example          |
| ---------- | ------ | -------------------- | ---------------- |
| first_name | string | first name of doctor | johan            |
| last_name  | string | last name of doctor  | doe              |
| email      | string | email string         | example@site.com |
| phone      | string | phone number of user | 09112834736      |
| slug       | string | user's unique slug   | johan123         |

## PhysiotherapyClinic

an Physiotherapy clinic is that kind of unit contains only physiotherapy doctors/nurses. here is the fields:

| title        | type          | description                                          | example                                        |
| ------------ | ------------- | ---------------------------------------------------- | ---------------------------------------------- |
| title        | string        | clinic title                                         | green house                                    |
| city         | [City](#city) | city of clinic                                       | -                                              |
| address_text | string        | address in plain text                                | st north. n 245                                |
| lon          | decimal(8, 6) | longtitude of clinic geo                             | 34.584758                                      |
| lat          | decimal(8, 6) | latitude of clinic geo                               | 42.384748                                      |
| phone        | string        | phone number                                         | 021483748                                      |
| mobile       | string        | mobile number. usually the secretary's mobile number | 092148574857                                   |
| slug         | string        | unique string to define the page of clinic           | greenee                                        |
| logo_url     | http url      | clinic logo url                                      | http://doctorsoal.com/units/84847273287384.png |

## Province

province is an object that defines the geo informations of a province

| title  | type            | description                                                  | example   |
| ------ | --------------- | ------------------------------------------------------------ | --------- |
| title  | string          | title of province                                            | paris     |
| lon    | decimal(8, 6)   | longtitude of province geo                                   | 34.584758 |
| lat    | decimal(8, 6)   | latitude of province geo                                     | 42.384748 |
| cities | [[City](#city)] | cities of province. it's nul when the parent model is a city | []        |

## Transaction