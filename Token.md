# `Token` Endpoint
URL: `https://www.drivethrurpg.com/api/v1/token`
Method: `POST`

Get access token, required for further operations.

## Authorization
Pass user API key in Header:
`"Authorization: Bearer <key>"`

## Passable Options
* `fields` ([[#Return Data|options]])

## Return Data
Field | Description
-----|-------------
`access_token` | Access token, used for authorization for further operations.
`customers_id` | Customer ID. Used to build URL for further operations.
`first_name` | Customer first name.
`last_name` | Customer last name.
`jwt` | [[https://jwt.io/#debugger-io\|JSON Web Token]]
