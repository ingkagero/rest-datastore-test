# rest-datastore-test

## Prerequisites

### EnvVars
```
GOOGLE_APPLICATION_CREDENTIALS=<credentials_file.json>
APP_ENGINE_PROJECT=<app_engine_project_identifier_string>
```
## Usage

### create user
```
curl --request POST \
  --url http://localhost:8080/api/users \
  --header 'content-type: application/json' \
  --data '{
	"name":"Jane Doe",
	"extra_property":"some property"
}'
```
### get all users
```
curl --request GET \
  --url http://localhost:8080/api/users \
  --header 'content-type: application/json'
```
### get users users with offset and limit
```
curl --request GET \
  --url 'http://localhost:8080/api/users?skip=5&limit=1' \
  --header 'content-type: application/json'
```
### equality filter users by property
```
curl --request GET \
  --url 'http://localhost:8080/api/users?filter=%7Bname%3A%22user%20seven%22%7D' \
  --header 'content-type: application/json'
```
### AND equality filter users by property
```
curl --request GET \
  --url 'http://localhost:8080/api/users?filter=%7B%24and%3A%20%5B%7Bname%3A%22user%20thirteen%22%7D%2C%7Bextra_property%3A%22property%20twelve%22%7D%5D%7D' \
  --header 'content-type: application/json'
```
### get id,extra_property for all users
```
curl --request GET \
  --url 'http://localhost:8080/api/users?fields=id%2Cextra_property' \
  --header 'content-type: application/json'
```
### delete users with offset and limit
```
curl --request DELETE \
  --url 'http://localhost:8080/api/users?skip=1&limit=1' \
  --header 'content-type: application/json'
```
### graphQL query by id
```
curl --request POST \
  --url http://localhost:8080/graphql \
  --header 'content-type: application/json' \
  --data '{"query":"{users(id:\"bojfgqauof2kcens4v5g\"){name,extra_property,created}}"}'
```
