
### Resumo dos Passos

1. **Executar os comandos `docker run` para ambos os contêineres:**
    - `docker run -d --name mongodb -p 27017:27017 mongo:4.2`
    - `docker run -d --name mongo-express --link mongodb:mongo -p 8081:8081 mongo-express`

