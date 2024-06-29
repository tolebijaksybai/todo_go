Todo List Go

Libraries

``` bash
go get github.com/sirupsen/logrus
go get github.com/gin-gonic/gin
go get github.com/jmoiron/sqlx
go get github.com/spf13/viper
go get github.com/lib/pq
go get github.com/joho/godotenv
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
