# Back-End-Architect
### Live Backend URL: https://build-week-sleep-tracker.herokuapp.com/
### **Register a user**
*method url*: `/api/auth/register`

*http method*: **[POST]**

#### Headers

| name           | type   | required | description              |
| -------------- | ------ | -------- | ------------------------ |
| `Content-Type` | String | Yes      | Must be application/json |

#### Body

| name           | type   | required | description              |
| -------------- | ------ | -------- | ------------------------ |
| `name`         | String | Yes      |                          |
| `lastName`     | String | Yes      |                          |
| `password`     | String | Yes      |                          |
| `email`        | String | Yes      | Must be unique           |
| `age`          | integer| No       |                          |

#### Example
```
{
	"email":"bpoltl@gmail.com",
	"password":"1234",
	"name":"Brooks",
	"lastName":"Poltl"
}
  ```

#### Response
##### 201 (created)

### **Login a user**
*method url*: `/api/auth/login`

*http method*: **[POST]**

#### Headers

| name           | type   | required | description              |
| -------------- | ------ | -------- | ------------------------ |
| `Content-Type` | String | Yes      | Must be application/json |

#### Body

| name           | type   | required | description              |
| -------------- | ------ | -------- | ------------------------ |
| `email`        | String | Yes      | must be registered email |
| `password`     | String | Yes      |                          |


#### Example
```
  {
    "email": "bpoltl@gmail.com",
    "password": "1234",
  }
  ```
  
 #### Response
##### 200 (ok)
> no issues logging in
###### Example response
```
{
    "message": "Logged In! Your ID is 5",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWJqZWN0Ijo1LCJlbWFpbCI6ImJwb2x0bEBnbWFpbC5jb20iLCJpYXQiOjE1NTU5NzAyMjMsImV4cCI6MTU1NjA1NjYyM30.lWi9hhalGt2ftr4Ju_jP12dCavZgXAMwABGYPzltwr8"
}
```
##### 401 (Unauthorized)
###### Example response
  ```
 { 
 message: "Please Provide Correct Credentials"
 }
 ```

### **get logged in users information**
*method url*: `/api/users`

*http method*: **[GET]**
#### Headers

| name           | type   | required | description              |
| -------------- | ------ | -------- | ------------------------ |
| `Content-Type` | String | Yes      | Must be application/json |
| `authorization`| String | Yes      | token to Authorize user  |

#### Response
##### 200 (ok)

###### Example response
```
[
    {
        "id": 5,
        "email": "bpoltl@gmail.com",
        "name": "Brooks",
        "lastName": "Poltl",
        "password": "$2a$04$FgiiacNirmVECdixfj8xau8rhnRAML6OfLPCPN1UCiq3xKO9m46UG",
        "age": null
    }
]
```
### **Edit a User Account**
*method url*: `/api/users/:id`

*http method*: **[PUT]**

#### Headers

| name           | type   | required | description              |
| -------------- | ------ | -------- | ------------------------ |
| `Content-Type` | String | Yes      | Must be application/json |
| `authorization`| String | Yes      | token to Authorize user  |
#### Body

| name           | type   | required | description              |
| -------------- | ------ | -------- | ------------------------ |
| `name`         | String | yes      |                          |
| `lastName`     | String | yes      |                          |
| `password`     | String | yes      |                          |
| `email`        | String | yes      |                          |
| `age`          | String | yes      |                          |

#### Example
```
{
        "email": "bpoltl@gmail.com",
        "name": "Brooks",
        "lastName": "smith",
        "password": "$2a$04$FgiiacNirmVECdixfj8xau8rhnRAML6OfLPCPN1UCiq3xKO9m46UG",
        "age": null
}
  ```
#### Response
##### 200 (ok)
###### Example Response
```
{
    "message": "Your Profile has been sucessfully updated!"
}
```
##### 403 (Forbidden)
###### Example Response
```
  {
  message: "You can't leave the required fields empty!"
  }
```
 ### **Delete an Account**
*method url*: `/api/users/:id`

*http method*: **[DELETE]**

#### Headers

| name           | type   | required | description              |
| -------------- | ------ | -------- | ------------------------ |
| `Content-Type` | String | Yes      | Must be application/json |
| `authorization`| String | Yes      | token to Authorize user  |

#### Response
##### 200 (ok)
###### Example Response
```
{
    "message": "User has been Deleted"
}
```
##### 404 (not found)
