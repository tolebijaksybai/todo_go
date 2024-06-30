Todo List Go

## Installation

1. Clone the repository from GitHub:
    ```bash
    https://github.com/tolebijaksybai/todo_go.git
    ```
2. Navigate into the project directory:
    ```bash
    cd todo_go
    ```
3. Copy the `.env.example` file to `.env` and modify it with your own values:
    ```bash
    cp .env.example .env
    ```
   Open the `.env` file and replace the placeholders with your actual values.

4. Up database Postgres
     ```bash
    docker pull posgress
    docker run --name=todo-db -e POSTGRES_PASSWORD='qwerty' -p 5436:5432 -d --rm postgres
   
    migrate -path ./schema/ -database 'postgres://postgres:qwerty@localhost:5436?sslmode=disable' up
    ```
   
Libraries

``` bash
go get github.com/gin-gonic/gin
go get github.com/jmoiron/sqlx
go get github.com/spf13/viper
go get github.com/lib/pq
go get github.com/joho/godotenv
go get github.com/sirupsen/logrus
go get -u github.com/golang-jwt/jwt/v5
```

Commands

``` bash
go run ./cmd/main.go

docker pull posgress
docker run --name=todo-db -e POSTGRES_PASSWORD='qwerty' -p 5436:5432 -d --rm postgres

migrate create -ext sql -dir ./schema -seq init
migrate -path ./schema/ -database 'postgres://postgres:qwerty@localhost:5436?sslmode=disable' up

docker exec -it 6c0fadb02359 bash
psql -U postgres
\d

select * from schema_migrations;
update schema_migrations set version='000001', dirty=false;
migrate -path ./schema/ -database 'postgres://postgres:qwerty@localhost:5436?sslmode=disable' down
```
## APIs

### Auth

#### Register User
- **Endpoint:** `POST /auth/sign-up`
- **Example request body:**
    ```json
    {
      "name": "Tolebi",
      "username": "tolebi",
      "password": "qwerty"
    }
    ```
- **Example response:**
    ```json
    HTTP/1.1 201 Created
    Content-Type: application/json

    {
      "id": 1
    }
    ```
#### Login User
- **Endpoint:** `POST /auth/sign-in`
- **Example request body:**
    ```json
    {
      "username" : "tolebi",
      "password" : "qwerty"
    }
    ```
- **Example response:**
    ```json
    HTTP/1.1 200 HTTP OK
    Content-Type: application/json

    {
      "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3MTk3OTAxODcsImlhdCI6MTcxOTc0Njk4NywidXNlcl9pZCI6MX0.WeRMEKDjHUmXvS--sWeYmUqHnD-WyfvxZnYjfbJEcrQ"
    }
    ```
#### Create List
- **Endpoint:** `POST /api/lists`
- **Example request body:**
    ```json
     "Authorization": "Bearer token"
  
    {
      "title" : "Список продуктов",
      "description" : "Купи себе нормалный"
    }
    ```
- **Example response:**
    ```json
    HTTP/1.1 201 Created
    Content-Type: application/json
  
    {
      "id": 3
    }
    ```
#### Get All Lists
- **Endpoint:** `GET /api/lists`
- **Example request body:**
    ```json
    "Authorization": "Bearer token"
    ```
- **Example response:**
    ```json
    HTTP/1.1 200 HTTP OK
    Content-Type: application/json
  
    {
        "data": [
            {
                "id": 1,
                "title": "Список продуктов",
                "description": ""
            }
        ]
    }
    ```