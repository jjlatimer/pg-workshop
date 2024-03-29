This is `pg-workshop`, the containerized workshop for PostgreSQL!

Generic postgres and pgadmin stack:

```
version: "3.1"

services:

  postgres:
    restart: always
    image: postgres
    container_name: demo-postgres #you can change this
    environment:
      - POSTGRES_USER=demo
      - POSTGRES_PASS=demo
      - POSTGRES_DB=demo
      - POSTGRES_PORT=5432
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data/

  pgadmin:
      image: dpage/pgadmin4
      container_name: demo-pgadmin #you can change this
      depends_on:
        - postgres
      ports:
        - "5051:80"
      environment:
        PGADMIN_DEFAULT_EMAIL: pgadmin4@pgadmin.org
        PGADMIN_DEFAULT_PASSWORD: root
      restart: always


volumes:
  postgres_data:
```

Source: https://dev.to/mojemoron/how-to-connect-your-django-app-to-a-dockerized-postgresql-and-pgadmin-133o
