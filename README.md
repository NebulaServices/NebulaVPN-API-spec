# NebulaVPN API specification

## TODO: organize
## TODO: generate sexy apidoc?

## GET `/api/server`
Responses: `string` (server codename)

Returns the codename of the server recommended for your client to connect to.

If the user is premium, they can add the optional parameter `?location=XX`, with `XX` as a country code supported by NebulaVPN which is in their plan: `US`, `UK`, `DE`, `JP`

## GET `/api/motd`
Responses: `string`

Returns a user-submitted MOTD for the client.

## GET `/api/plan`
Parameters: `string` (token)

Responses: 
```
Object {
  type: string,
  paid_to: integer
}
```

Returns the current type of plan (`free`, `starter`, `advanced`), and when the plan expires (UNIX timestamp of when it will expire, `0` if the user has a `free` plan).  

## POST `/api/login`
Parameters: `string` (token)

Responses: `string` (token), `null`

Returns a token if the login was valid, and returns `null` if the login was not valid.

## POST `/api/createAccount`
Parameters: `string` (token)

Responses: `string` (token)

Returns a token. Defers to `/api/login` if the token already is in the database
