# realname-api

Public API interface provided by bazar Realname service.

## Version

0.1

## API definition

- API list

    |Url|Description|
    |-|-|
    |[/Realname/RegisterUser](#registeruser)|register a user with realname information|
    |[/Realname/GetRegister](#getregister)|get register request of a user|
    |[/Realname/CancelRegister](#cancelregister)|cancel register request of a user|
    |[/Realname/UpdateUser](#updateuser)|update user realname info|
    |[/Realname/GetUserInfo](#getuserinfo)|get realname info of user|

- RegisterUser

    POST [RegisterRequest](#registerrequest)

    RESPONSE [ApiResponse](#apiresponse)<string> with requestID

- GetRegister

    GET with queryString "?requestID=xxxx&signature=xxxx"

    RESPONSE ApiResponse<[RegisterRequestDto](#RegisterRequestDto)>

- CancelRegister

    POST with queryString "?requestID=xxxx&signature=xxxx"

    RESPONSE ApiResponse

- UpdateUser

    POST [RegisterRequest](#registerrequest)

    RESPONSE ApiResponse

- GetUserInfo

    Get with queryString "?userID=xxxx"

    RESPONSE ApiResponse<[UserRealnameInfo](#userrealnameinfo)>

## Entities



- RegisterRequest

    This is a commandConntent inside [UserCommand](https://github.com/bazarinitiative/bazar-protocol-doc/blob/main/BazarProtocol.md#Command)

    | Field | FieldType | Required | Comment |
    |-|-|-|-|
    |userID|char(30)|Y|userID in bazar system|
    |displayName|varchar(30)|Y|display name of this realname user|
    |socialUrl|varchar(100)|Y|social url for confirmation, user can post something with his existing social account to finish this realname authorization. |
    |advanceInfo|varchar(1000)|Y|advanced information to finish this realname authorization. |

- RegisterRequestDto
    | Field | FieldType | Required | Comment |
    |-|-|-|-|
    |requestID|varchar(30)|uniqueID for this request|
    |userID|char(30)|Y|userID in bazar system|
    |displayName|varchar(30)|Y|display name of this realname user|
    |socialUrl|varchar(100)|Y|social url for confirmation, user can post something with his existing social account to finish this realname authorization. |
    |advanceInfo|varchar(1000)|Y|advanced information to finish this realname authorization. |
    |requstTime|long|timestamp in milli|
    |status|char|I: init, P: processing, F: failed, S: succeed|

- UserRealnameInfo

    | Field | FieldType | Required | Comment |
    |-|-|-|-|
    |userID|char(30)|Y|userID in bazar system|
    |displayName|varchar(30)|Y|display name of this realname user|

- ApiResponse

    | Field | FieldType | Required | Comment |
    |-|-|-|-|
    |success|bool|Y||
    |msg|varchar(100)|Y||
    |data|object|Y|response data if any|
