---
description: >-
  All credits and materials belong to -
  https://github.com/42-AI/bootcamp_data-engineering. This gitbook was put
  together just to make the material easier to read.
---

# README

## The client-server architecture

 Bootcamp Data Engineering

PostgreSQL is an open-source database which follows a client-server architecture. It is divided in three different components :

 One week to learn Data Engineering :rocket:   


* a **client**, a program on the user's machine which communicates the user's query to the server and receives the server's answers. 
* a **server**, a program running in the background that manages access to a specific resource, service or network. The server will understand the client's query and apply it to the database. Then it will send an answer to the client.
* a **database system**, where the data is stored.

### Table of Contents

{width=600px}

* [Curriculum](./#curriculum)
  * [Module00 - PostgreSQL](./#Module00---postgresql)
  * [Module01 - Elasticsearch](./#Module01---elasticsearch)
  * [Module02 - AWS](./#Module02---aws)
  * [Module03 - Hadoop](./#Module03---spark)
  * [Module04 - Spark](./#Module04---airflow)
* [Acknowledgements](./#acknowledgements)
  * [Contributors](./#contributors)

ps: client and server can be located on the same machine

This project is a Data Engineering bootcamp created by [42 AI](http://www.42ai.fr).

In the case of PostgreSQL, we are going to use `psql` as a client and `pg_ctl` for the server.

A prior Python programming experience is required \(the Python bootcamp\)! Your mission, should you choose to accept it, is to come and learn some of the essential knowledge for Data Engineering, in a single week. You will start with SQL and NoSQL languages and then get acquainted with some useful tools/frameworks for Data Engineering like Airflow, AWS and Spark.

## PostgreSQL install

42 Artificial Intelligence is a student organization of the Paris campus of the school 42. Our purpose is to foster discussion, learning, and interest in the field of artificial intelligence, by organizing various activities such as lectures and workshops.

The first thing we need to do is install PostgreSQL.

## Curriculum

```bash
brew install postgresql
```

### Module00 - PostgreSQL

nb: if you notice any problem with brew, you can reinstall it with the following command.

**Let's get started with PostgreSQL!** :link:

```bash
rm -rf $HOME/.brew && git clone --depth=1 https://github.com/Homebrew/brew $HOME/.brew && echo 'export PATH=$HOME/.brew/bin:$PATH' >> $HOME/.zshrc && source $HOME/.zshrc && brew update
```

> Filter Data, Normalize Data, Populate tables, Data Analysis ...

The next thing we need to do is export a variable `PGDATA`. We can add the following line to our `.zshrc` file.

### Module01 - Elasticsearch

```bash
export PGDATA=$HOME/.brew/var/postgres
```

**Get acquainted with Elasticsearch** :mag\_right:

and source the .zshrc.

> Elasticsearch setup, Data Analysis, Aggregations, Kibana and Monitoring ...

```bash
source ~/.zshrc
```

### Module02 - AWS

Now, we can start the postgresql server. A server is a program running in the background that manages access to a specific resource, service or network. As you guessed, the postgresql allows us to access a database here.

**Start exploring the cloud on AWS!** :cloud:

We can start the server.

> Discover AWS, Flask APIs and infrastructure provisioning with Terraform ...

```bash
$> pg_ctl start
waiting for server to start....2019-12-08 15:58:21.171 CET [84406] LOG:  starting PostgreSQL 12.1 on x86_64-apple-darwin18.6.0, compiled by Apple LLVM version 10.0.1 (clang-1001.0.46.4), 64-bit
2019-12-08 15:58:21.173 CET [84406] LOG:  listening on IPv6 address "::1", port 5432
2019-12-08 15:58:21.173 CET [84406] LOG:  listening on IPv4 address "127.0.0.1", port 5432
2019-12-08 15:58:21.174 CET [84406] LOG:  listening on Unix socket "/tmp/.s.PGSQL.5432"
2019-12-08 15:58:21.192 CET [84407] LOG:  database system was shut down at 2019-12-08 15:49:49 CET
2019-12-08 15:58:21.201 CET [84406] LOG:  database system is ready to accept connections
 done
server started
```

### Module03 - Hadoop

We notice the postgreSQL is associated with the port `5432`.

**Work in progress**

`pg_ctl stop` can stop the server.

### Module04 - Spark

A server program is often associated with a client. Our client here is called `psql`. In the beginning, only one database exists, `postgres`. We must use that database first to access the postgresql console.

**Work in progress**

```bash
$> psql -d postgres
psql (12.1)
Type "help" for help.

postgres=#
```

## Acknowledgements

`\?` allows you to see all the possible commands in the PostgreSQL console. The first thing we can do is list the databases with `\l`.

### Contributors

```text
postgres=# \l
                          List of databases
   Name    | Owner  | Encoding | Collate | Ctype | Access privileges
-----------+--------+----------+---------+-------+-------------------
 postgres  | fbabin | UTF8     | C       | C     |
 template0 | fbabin | UTF8     | C       | C     | =c/fbabin        +
           |        |          |         |       | fbabin=CTc/fbabin
 template1 | fbabin | UTF8     | C       | C     | =c/fbabin        +
           |        |          |         |       | fbabin=CTc/fbabin
(3 rows)
```

* Francois-Xavier Babin \(fbabin@student.42.fr\)
* Jeremy Jauzion \(jjauzion@student.42.fr\)
* Myriam Benzarti \(mybenzar@student.42.fr\)
* Mehdi Aissa Belaloui \(mbelalou@student.42.fr
* Eren Ozdek \(eozdek@student.42.fr\)

We are going to create a database for the day.

```bash
postgres=# CREATE DATABASE appstore_games;
```

Add a user with a very strong password!

```bash
postgres=# CREATE USER postgres_user WITH PASSWORD '12345';
```

We must alter the database \(changes the attributes of a database\) to allow access only for us.

```bash
postgres=# ALTER DATABASE appstore_games OWNER TO postgres_user;
```

The last thing we need to do is edit the `~/.brew/var/postgres/pg_hba.conf` file to modify the following line.

```text
host    all        all        127.0.0.1/32        trusted
```

to

```text
host    all        all        127.0.0.1/32        md5
```

This modification will force the use of the password to connect to the database.

We are ready to use Postgres!

## Pyenv install

Dealing with Python is often hell when it comes to python versions and libraries version. This problem is often encountered few people are working on the same server with different library needs. Furthermore you don't want to mess with the system python. That's why virtual environments and separated python are a preferred solution.

You can install pyenv with brew using the following command.

```text
brew install pyenv
```

All the python candidates can then be listed.

```text
pyenv install --list | grep " 3\.[678]"
```

... and installed. For the day we are going to choose version `3.8.0`.

```text
pyenv install -v 3.8.0
```

Finally the installed version can be activated through this command.

```text
pyenv global 3.8.0
```

Don’t forget to add those lines to your .zshrc file in order to activate your python environment each time you open a terminal.

```text
export PATH="/home/misteir/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"

pyenv global 3.8.0 #activate the python 3.8.0 as default python
```

## Pipenv install

Pipenv is a tool to handle packages versions of an environment. This tool is very similar to the `requirements.txt` file with some extra metadata.

Pipenv can be installed with this simple command.

```text
pip install pipenv
```

You can find a toml file for the day named `Pipfile`.

```text
[[source]]
url = "https://pypi.python.org/simple"
verify_ssl = true
name = "pypi"

[packages]
jupyter = "*"
numpy = "*"
pandas = "*"
psycopg2 = "*"

[requires]
python_version = "3.8.0"
```

To setup your environment just follow these two steps.

```text
pipenv install
pipenv shell
```

You have now PostgreSQL, virtual python and requirements installed and ready for the day!

