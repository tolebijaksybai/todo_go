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

#### Register a new user
- **Endpoint:** `POST /auth/sign-up`
- **Description:** Create a new user. The request body should contain the user information in JSON format.
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
