---
title: 'MySQL with Docker Compose'
excerpt: 'Hi! I want to share a very simple way to create a MySQL instance using Docker Compose. Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Praesent elementum facilisis leo vel fringilla est ullamcorper eget. At imperdiet dui accumsan sit amet nulla facilities morbi tempus.'
coverImage: 'https://dev-to-uploads.s3.amazonaws.com/i/upqkgnyo34qtccv6vxoo.jpg'
date: '2020-10-21T23:35:00.322Z'
author:
  name: Rodolfo Chaves Fernandes
  picture: '/assets/blog/authors/rodolfo.png'
ogImage:
  url: 'https://media.gettyimages.com/videos/dusky-dolphin-somersaults-new-zealand-video-id1156443605?s=640x640'
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
