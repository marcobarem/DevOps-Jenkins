### Resumo dos Passos

1. **Executar os comandos `docker run` para ambos os contêineres:**
    - `docker run -d --name mariadb -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 mariadb`
    - `docker run -d --name phpmyadmin --link mariadb:db -p 8080:80 phpmyadmin/phpmyadmin`
