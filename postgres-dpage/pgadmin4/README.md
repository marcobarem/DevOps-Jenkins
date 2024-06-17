
#### Exercício 3

```markdown
# Exercício 3: postgres e dpage/pgadmin4

## Parâmetro de execução de container (docker run)

### Comando para postgres:
```bash
docker run -d --name postgres -e POSTGRES_PASSWORD=root -p 5432:5432 postgres
