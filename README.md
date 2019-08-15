Learning how to add a PostgreSQL database in a Docker container to a
Ruby program by rewiring the Expenses app.
***
### Setup

- have docker installed
- build your containter:
  `$ docker run --name ruby-postgres -e POSTGRES_PASSWORD=mysecret -d -p 5432:5432 postgres`
- Go inside your container and create a database `expenses`:
```
$ docker exec -it ruby-postgres bash
root@05b3a3471f6f:/# psql -U postgres
postgres-# CREATE DATABASE expenses;
postgres-# \q
exit
```
- ready to go: start the app

- Cleaning up when done:
Don't forget to clean up the container (and maybe the image too) before you go:

remove the container:
```
$ docker stop ruby-postgres
$ docker rm ruby-postgres
```
remove the postgres image:
```
$ docker rmi postgres
```
***
### Expenses app

Small command line application to track expenses

    An expense recording system

    Commands:

    add AMOUNT MEMO [DATE] - record a new expense
    clear - delete all expenses
    list - list all expenses
    delete NUMBER - remove expense with id NUMBER
    search QUERY - list expenses with a matching memo field


run: `$ ./expense`

run a command: `$ ./expense add 4.50 coffee`




