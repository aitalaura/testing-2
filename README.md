# API Structure for Docker

## First API - after Boot Docker
**```API Type```** - POST
**```Endpoint```** - /api/docker/register
**```Content-Type```** - `application/json`
*request* -
>     {
>        "macAddress": "00:1B:44:11:3A:B7"
>     }
 

*response* -
>     {
>     status:true,
>     message:”Docker detail fetched”,
>     data:
>        {
>          "dockerId": "f6c9126d33a7",
>        }
>     } 


## Second API - When user clicks on get Info Button
**```API Type```** - POST
**```Endpoint```** - /api/docker/getInfo
**```Content-Type```** - `application/json`
*request* -
>     {
>        "dockerId": "xyz"
>     } 

*response* -
>     {
>     status:true,
>     message:”Docker detail fetched”,
>     data:
>        {
>          "companyName": "Acme Corp",
>          "displayName": "ACME Server",
>          "storeId": "123456”
>        }
>     } 



## Third API - when user enter 6 digit code
**```API Type```** - POST
**```Endpoint```** - /api/salesPerson/login
**```Content-Type```** - `application/json`
*request* -
>     {
>        "code": "123456",
>        "dockerId":"xyz"
>     } 


*response* -
>     {
>     status:true,
>     message:”sales person's details fetched”,
>     data:
>        {
>          "name": "Manoj",
>          "email":"manoj@ymail.com",
>        }
>     } 


## Four API - when user undock wearable
**``Note = 1. [When user try to unmount wearable without entering code error message should be display "Unauthorized Access"]
2. [User Info file will be created on wearable]``** 
**```API Type```** - POST
**```Endpoint```** - /api/wearable/unmount
**```Content-Type```** - `application/json`
*request* -
>     {
>        "email": "manoj@ymail.com",
>        "wearableId":"xyz", //wearable id can be found from text file stored on device named "DEVID.txt" - DEVICEID:<DeviceID>
>        "dockerId":"zyt",
>        "wearableMacAddress":"xyz"
>     } 


*response* -
>     {
>     status:true,
>     message:”Wearable unmount successfully”,
>     data:
>        {
>        }
>     } 


## Five API - when user redock wearable

**```API Type```** - POST
**```Endpoint```** - /api/wearable/remount
**```Content-Type```** - `application/json`
*request* -
>     {
>        "email": "manoj@ymail.com",
>        "wearableId":"xyz",
>        "dockerId":"zyt"
>     } 


*response* -
>     {
>     status:true,
>     message:”Wearable Remount successfully”,
>     data:
>        {
>            "bucketName":"talaura-docker-bucket",
>            "awsAccessKeyId":"AKIAXY7JWHKMKT6UESQ7",
>            "awsSecretAccessKey":"RUyvbnFN37XuTNqw9iKvHCndjcY",
>            "bucketUrl":"s3://talaura-docker-bucket/nayka/storeName/"
>        }
>     } 


## Six API - when file upload process 

**``Note = when uploading the files ``** 

**```API Type```** - POST
**```Endpoint```** - /api/wearable/uploaddata
**```Content-Type```** - `application/json`
*request* -
>     {
>        "email": "manoj@ymail.com",
>        "wearableId":"xyz",
>        "dockerId":"zyt",
>        "numberofFiles" : 5,
>        "totalFileSize" : "50KB",
>        data:
>        {
>            "bucketName":"talaura-docker-bucket",
>            "awsAccessKeyId":"AKIAXY7JWHKMKT6UESQ7",
>            "awsSecretAccessKey":"RUyvbnFN37XuTNqw9iKvHCndjcY",
>            "bucketUrl":"s3://talaura-docker-bucket/<companydisplayname>/<storeId>/"
>        }
>     } 


*response* -
>     {
>     status:true,
>     message:”Data Upload Acknowledged”,
>     data:
>        {
>         
>        }
>     } 
