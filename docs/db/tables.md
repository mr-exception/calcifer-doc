# Tables

here is a complete list of tables in db:

## activity_times

| name                  | type          | default       | description                                                               |
| ---                   | ---           | ---           | ---                                                                       |
| id                    | uuid          | -             | primary id                                                                |
| day_of_week           | smallint(6)   | -             | the day of week from 1 to 7                                               |
| start_time            | integer(11)   | -             | hour and minute of day in timestamps                                      |
| finish_time           | integer(11)   | -             | hour and minute of day in timestamps                                      |
| unit_user_id          | uuid          | -             | relation to [unit_user](#unit_user)                                       |
| status                | smallint(6)   | 1             | [status](#activity_times_status)                                          |
| auto_fill             | smallint(6)   | 0             | [autofill](#activity_times_auto_fill)                                     |
| just_in_unit_visit    | smallint(6)   | 1             | [just in unit visit](#activity_times_just_in_unit_visit)                  |
| demand_limit          | smallint(6)   | 0             | [demand limit](#activity_times_demand_limit)                              |
| default_price         | integer(11)   | 0             | default price for each demand                                             |
| default_deposit       | integer(11)   | 0             | default deposit for each demand                                           |
| default_demand_time   | integer(11)   | 0             | default time set for each demand                                          |
| created_at            | timestamps    | CURRENT_TIMESTAMPS    | when the row created                                              |
| modified_at           | timestamps    | CURRENT_TIMESTAMPS    | the last time row modified                                        |

## addresses
## bank_accounts
## bids
## cities
## consts
## demands
## demand_attachments
## demand_event_attachments
## doctors
## entries
## experiments
## experiment_fields
## migrations
## notifications
## nurses
## off_times
## password_resets
## patients
## permissions
## provinces
## report_fields
## report_templates
## transactions
## units
## unit_user
## users