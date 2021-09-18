# Authentication
The Authentication API enables you to manage all aspects of user identity when you use Auth. It offers endpoints so your users can log in, log out, access APIs, and more.

## **BearerAuth**
The authorization token for this account. It's gives access to the bearer. This token should be kept a secret, so no sharing. Its expires in 24hours.

|  |  |
| ----------- | ----------- |
| Security Scheme Type | HTTP |
| HTTP Authorization Scheme | bearer|
| Bearer format | "JWT"|
|  |  |
## **CookieAuth**
It authorizes clients request and maintains session information. Its expires in 24hours.

|  |  |
| ----------- | ----------- |
| Security Scheme Type | API KEY |
| Cookie parameter name: | JSESSIONID|
|  |  |



## **Errors**
When an error occurs, you will receive an error object. Most of these error objects contain an error code and an error description so that your applications can more efficiently identify the problem.

If you get a 4xx response code, then you can assume that there is a bad request from your end. In this case, 
check the [Standard Error Responses](#standard-error-responses) for more context.

5xx errors suggest a problem on server's end.

# Organization Members  
 
## Get a list of members in an organization: 
To get a list of members in an organization, send a **GET** request to this **Endpoint** `https://api.zuri.chat/organizations/{organization_id}/members/`
along with aunthentication(cookieAuth/bearerAuth) in the request header for authorization.
Replace `{organization_id}` with the Id of the organization you want to list its members. 
> e.g.  `https://api.zuri.chat/organizations/6137d69b21d3c78fc9a84bdf/members/`. 

*The response returns a success 200 code and the list of all members in the specified organization Id in json format and an empty array if there are no members* 
## Response Sample
**Content type** 
application/json
```sh
{
"code": 200,
"message": "string",
+ "data": {}
}
```
 
 
## Add user to an organization: 
To add a user to an organization, send a **POST** request to this **Endpoint** 
`https://api.zuri.chat/organizations/{organization_id}/members`, along with aunthentication(cookieAuth/bearerAuth) in the request header for authorization. 
Replace `{organization_id}` with the Id of the organization you want to add a user. 
> e.g. `https://api.zuri.chat/organizations/6137d69b21d3c78fc9a84bdf/members/` 
## Request body Sample
**content type** 
application/json
```sh
{ “user_id”: “6137d69b21d3c78fc9a84bdf” }
``` 
*The response returns a success 201 code and confirmation data in json format.* 
## Response Sample
**Content type** 
application/json
```sh
{
  "code": 201,
  "message": "string",
  "data": {
    "InsertedID": "6137d69b21d3c78fc9a84bdf"
  }
}
```


## Get a record of a member in an organization:  
To get a record of a member in an organization, send  a **GET** request to this **Endpoint** `https://api.zuri.chat/organizations/{organization_id}/members/{member_id}` along with aunthentication(cookieAuth/bearerAuth) in the request header for authorization. 
Replace `{organization_id}` with the Id of the organization you want to fetch a member record from and replace {member_id} with the Id of the member you want to get their record.
> e.g. `https://api.zuri.chat/organizations/6137d69b21d3c78fc9a84bdf/members/6137d69b21d3c78fc9a84bdf`

*The response returns a 200 success code and the full record of the specified member in json format.* 
## Response Sample
**Content type** 
application/json
```sh
{
  "code": 200,
  "message": "string",
  "data": {
    "_id": "6137d69b21d3c78fc9a84bdf",
    "orgId": "6137d69b21d3c78fc9a84bdf",
    "files": {},
    "image_url": "https://image.location/image.png",
    "name": "string",
    "status": "string",
    "email": "user@example.com",
    "display_name": "string",
    "bio": "string",
    "pronouns": "string",
    "phone": "string",
    "time_zone": "string",
    "joined_at": "2019-08-24"
  }
}
```

## Update user:
To update user a users's organization information e.g. user roles and permissions send a **PUT** request to this **Endpoint** `https://api.zuri.chat/organizations/{organization_id}/members/{member_id}` along with aunthentication(cookieAuth/bearerAuth) in the request header for authorization. 
Replace `{organization_id}` with the Id of the organization you want to fetch a member record from and replace `{member_id}` with the Id of the member you want to update their record.
> e.g. `https://api.zuri.chat/organizations/6137d69b21d3c78fc9a84bdf/members/6137d69b21d3c78fc9a84bdf`

Then in the body of the request provide the key-value pair of the item you want to update in the member record in json format. 
## Request body Sample
**content type** 
application/json
```sh
e.g. { “data”: “2” } 
```
*The response returns a success 200 code and confirmation data in json format* e.g.
## Response Sample
**content type** 
application/json
```sh
{
  "code": 200,
  "message": "resource updated successfully"
}
```

## Delete user:
To delete a user from an organization send a **DELETE** request to this **Endpoint** `https://api.zuri.chat/organizations/{organization_id}/members/{member_id}` along with aunthentication(cookieAuth/bearerAuth) in the request header for authorization. 
Replace `{organization_id}` with the Id of the organization you want to delete a user from and replace `{member_id}` with the Id of the user you want to delete.
> e.g. `https://api.zuri.chat/organizations/6137d69b21d3c78fc9a84bdf/members/6137d69b21d3c78fc9a84bdf`

*The response returns a success 200 code and confirmation data in json format.* 
## Response Sample
**content type** 
application/json
```sh
{
  "code": 200,
  "message": "resource updated successfully"
}
```


## Update member status for an organization:
To update member status of  a member of an organization send a **PATCH** request to this **Endpoint**
 `https://api.zuri.chat/organizations/{organization_id}/members/{member_id}/status`
along with aunthentication(cookieAuth/bearerAuth) in the request header for authorization. 
Replace `{organization_id}` with the Id of the organization you want to update it's member status and replace `{member_id}` with the Id of the member you want to update their status.
> e.g. `https://api.zuri.chat/organizations/6137d69b21d3c78fc9a84bdf/members/6137d69b21d3c78fc9a84bdf/status`
Then in the body of the request provide the status and its value in json format. 
## Request Body Sample
**content type** 
application/json
```sh
e.g. { “status”: “Available” } 
```
*The response returns a success 200 code and confirmation data in json format.* 
## Response Sample
**content type** 
application/json
```sh
{
  "code": 200,
  "message": "resource updated successfully"
}
```

## Update member profile picture for an organization:
To update profile picture  of  a member of an organization send a **PATCH** request to this **Endpoint** `https://api.zuri.chat/organizations/{organization_id}/members/{member_id}/photo` along with aunthentication(cookieAuth/bearerAuth) in the request header for authorization. 
Replace `{organization_id}` with the Id of the organization you want to update the profile picture of  it's member and replace `{member_id}` with the Id of the member you want to update their profile picture.
> e.g. `https://api.zuri.chat/organizations/6137d69b21d3c78fc9a84bdf/members/6137d69b21d3c78fc9a84bdf/photo`

Then in the body of the request provide "image_utl" and the image link as a key-value pair in json format. 
## Request Body Sample
**content type** 
application/json
```sh
{ “image_utl”: “https://image.storage/image.png” } 
```
*The response returns a success 200 code and confirmation data in json format.* 
## Response Sample
**content type** 
application/json
```sh
{
  "code": 200,
  "message": "resource updated successfully"
}
```

## Update member profile for an organization:
To update profile of a member of an organization send a **PATCH** request to this **Endpoint** `https://api.zuri.chat/organizations/{organization_id}/members/{member_id}/profile` along with aunthentication(cookieAuth/bearerAuth) in the request header for authorization. 
Replace `{organization_id}` with the Id of the organization you want to update the profile of  it's member and replace `{member_id}` with the Id of the member you want to update their profile.
> e.g. `https://api.zuri.chat/organizations/6137d69b21d3c78fc9a84bdf/members/6137d69b21d3c78fc9a84bdf/profile`

Then in the body of the request provide the key-value pair of the item you want to update in json format.
## Request Body Sample
**content type** 
application/json
```sh
e.g. { “data”: “string” } 
```
*The response returns a success 200 code and confirmation data in json format.* 
## Response Sample
**content type** 
application/json
```sh
{
  "code": 200,
  "message": "resource updated successfully"
}
```

## Toggle a member presence (Away/Active):
To update profile of a member of an organization send a **POST** request to this **Endpoint** `https://api.zuri.chat/organizations/{organization_id}/members/{member_id}/presence` along with aunthentication(cookieAuth/bearerAuth) in the request header for authorization. 
Replace `{organization_id}` with the Id of the organization you want to toggle the presence status of  it's member and replace `{member_id}` with the Id of the member you want to toggle their presence status.
> e.g. `https://api.zuri.chat/organizations/6137d69b21d3c78fc9a84bdf/members/6137d69b21d3c78fc9a84bdf/presence`

*The response returns a success 200 code and confirmation data in json format.* 
## Response Sample
**content type** 
application/json
```sh
{
  "code": 200,
  "message": "resource updated successfully"
}
```

## update a member settings field(s):
To update a member settings field(s) in an organization send a **PATCH** request to this **Endpoint** `https://api.zuri.chat/organizations/{organization_id}/members/{member_id}/settings` along with aunthentication(cookieAuth/bearerAuth) in the request header for authorization. 
Replace `{organization_id}` with the Id of the organization you want to update it's member settings field(s) and replace `{member_id}` with the Id of the member you want to update their settings field(s).
> e.g. `https://api.zuri.chat/organizations/6137d69b21d3c78fc9a84bdf/members/6137d69b21d3c78fc9a84bdf/settings`

Then in the body of the request provide the key-value pair of the settings you want to update in json format. 
## Request Body Sample
**content type** 
application/json
```sh
 { 
- “global_settings”: {
                “allow_user_add_plugins”:true,
                 "allow_only_admin_invite":true
               } ,
- "plugin_settings": {
       + "chess_plugin": {...}
       }
}
```
*The response returns a success 200 code and confirmation data in json format.*
## Response Sample
**content type** 
application/json
```sh
{
  "code": 200,
  "message": "resource updated successfully"
}
```


## Standard Error Responses 
The Authentication API may return the following HTTP Status Codes:

---

### **400**  An icorrect client request <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string

 ```



### **401** Is the error that shows up because the request is unauthorized <br>

```
 RESPONSE SCHEMA:   application/json

code required        integer <int32>
message required     string


```

 ### **422** Server unable to process contained information e.g API behavior <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 

```

### **500** Comes up when internal server error occured during operation

```

RESPONSE SCHEMA:     application/json

code required         integer <int32>
message required      string

```











