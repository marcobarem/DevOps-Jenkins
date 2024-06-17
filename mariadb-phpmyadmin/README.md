
#### Exercício 2

```markdown
# Exercício 2: mariadb e phpmyadmin

## Parâmetro de execução de container (docker run)

### Comando para mariadb:
```bash
docker run -d --name mariadb -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 mariadb
