---
title: 'MySQL with Docker Compose'
excerpt: 'Hi! I want to share a very simple way to create a MySQL instance using Docker Compose.'
coverImage: 'https://dev-to-uploads.s3.amazonaws.com/i/fsf104dlrudu424bd8xq.png'
date: '2020-09-21T23:35:00.322Z'
author:
  name: Rodolfo Chaves Fernandes
  picture: '/assets/blog/authors/joe.jpeg'
ogImage:
  url: 'https://dev-to-uploads.s3.amazonaws.com/i/fsf104dlrudu424bd8xq.png'
---

Hey Folks!

I want to share a very simple way to create a MySQL instance using Docker Compose.

Create a file named `docker-compose.yml` with the code bellow. You should replace the `<secret_pass>` to a safe password for MySQL root username.

```yaml
version: '3.1'
services:

  mysql_db:
    image: mysql
    restart: always
    container_name: mysql_container
    environment:
      MYSQL_ROOT_PASSWORD: <secret_pass>
    ports:
      - "3306:3306"
    volumes:
      - mysql_db_data:/var/lib/mysql

volumes:
  mysql_db_data:
```

Type in your terminal `docker-compose up` to start and `docker-compose down` to stop the container.
Use `docker rm mysql_container -f` if you want to remove the container.

You can use MySQL Workbench to access the database using the username as root and password as `<secret_pass>`.

But if you want to simplify the data visualization is possible to use an Adminer container, see:

```yaml
version: '3.1'
services:

  mysql_db:
    image: mysql
    restart: always
    container_name: mysql_container
    environment:
      MYSQL_ROOT_PASSWORD: <secret_pass>
    ports:
      - "3306:3306"
    volumes:
      - mysql_db_data:/var/lib/mysql
    networks:
      - mysql_network

  adminer:
    image: adminer
    ports:
      - 8006:8080
    networks:
      - mysql_network

volumes:
  mysql_db_data:

networks:
  mysql_network:
    driver: bridge
```

Access through [http://localhost:8006](http://localhost:8006) and use the credentials defined before.

Have fun!
