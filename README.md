# API Structure for Docker

## First API - after Boot Docker
**```API Type```** - POST
**```Endpoint```** - /api/docker/register
**```Content-Type```** - `application/json`
*request* -
>     {
>        "macAddress": "00:1B:44:11:3A:B7"
>     } 

**First Time Reponse - **
*response* -
>     {
>     status:true,
>     message:”Docker detail fetched”,
>     data:
>        {
>          "dockerId": "f6c9126d33a7",
>        }
>     } 

**Second Time Reponse - **
*response* -
>     {
>     status:true,
>     message:”Docker detail fetched”,
>     data:
>        {
>          "dockerId": "f6c9126d33a7",
>          "companyName": "Acme Corp",
>          "displayName": "ACME Server",
>          "storeId": "123456”
>        }
>     } 




## Second API - when user enter 6 digit code
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
>     message:”sales person's detail fetched”,
>     data:
>        {
>          "name": "Manoj",
>          "email":"manoj@ymail.com"
>        }
>     } 


## Third API - when user undock wearable
**``Note = 1. [When user try to unmount wearable without entering code error message should be display "Unauthorized Access"]
2. [User Info file will be created on wearable]``** 
**```API Type```** - POST
**```Endpoint```** - /api/wearable/unmount
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
>     message:”Wearable unmount successfully”,
>     data:
>        {
>            "bucketName":"talaura-docker-bucket",
>            "awsAccessKeyId":"AKIAXY7JWHKMKT6UESQ7",
>            "awsSecretAccessKey":"RUyvbnFN37XuTNqw9iKvHCndjcY",
>            "bucketUrl":"s3://talaura-docker-bucket/nayka"
>        }
>     } 


## Fourth API - when user redock wearable

**``Note = When user remount wearable to docker data will be uploaded to S3 and User Info detail will be deleted from wearable``** 

**```API Type```** - POST
**```Endpoint```** - /api/wearable/remount
**```Content-Type```** - `application/json`
*request* -
>     {
>        "email": "manoj@ymail.com",
>        "wearableId":"xyz",
>        "dockerId":"zyt",
>        "awsUrl":[]
>     } 


*response* -
>     {
>     status:true,
>     message:”Wearable Remount successfully”,
>     data:
>        {
>        }
>     } 
