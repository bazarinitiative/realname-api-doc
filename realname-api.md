# realname-api

Public API interface provided by bazar Realname service.

## Version

0.1

## API definition

    |Url|Description|
    |-|-|
    |[/Realname/RegisterUser](#RegisterUser)|register a user with realname information|
    |[/Realname/GetRegister](#getregister)|get register request of a user|
    |[/Realname/CancelRegister](#cancelregister)|cancel register request of a user|
    |[/Realname/UpdateUser](#updateuser)|update user realname info|
    |[/Realname/GetUserInfo](#getuserinfo)|get realname info of user|

### RegisterUser

POST [RegisterRequest](#registerrequest)

RESPONSE [ApiResponse](#apiresponse)

### GetRegister

GET with queryString "?userID=xxxx"

RESPONSE ApiResponse

### CancelRegister

POST with queryString "?userID=xxxx"

RESPONSE ApiResponse

### UpdateUser

POST [RegisterRequest](#registerrequest)

RESPONSE ApiResponse

### GetUserInfo

Get with queryString "?userID=xxxx"

RESPONSE ApiResponse<[UserRealnameInfo](#userrealnameinfo)>

## Entities

### RegisterRequest

    | Field | FieldType | Required | Comment |
    |-|-|-|-|
    |userID|char(30)|Y|userID in bazar system|
    |displayName|varchar(30)|Y|display name of this realname user|
    |socialUrl|varchar(100)|Y|social url for confirmation, user can post something with his existing social account to finish this realname authorization. |
    |advanceInfo|varchar(1000)|Y|advanced information to finish this realname authorization. |

### UserRealnameInfo

    | Field | FieldType | Required | Comment |
    |-|-|-|-|
    |userID|char(30)|Y|userID in bazar system|
    |displayName|varchar(30)|Y|display name of this realname user|

### ApiResponse

    | Field | FieldType | Required | Comment |
    |-|-|-|-|
    |success|bool|Y||
    |msg|varchar(100)|Y||
    |data|object|Y|response data if any|
