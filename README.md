# Projeto conversão de distância

### Sobre o projeto
O projeto conversão de distância é um projeto desenvolvido em Python. O projeto tem como objetivo ser um exemplo para a criação de ambiente com containers usando Python.

### Observações do projeto
A aplicação é exposta:<br>
**docker compose:** usando a porta 5000 <br>
**Kubernetes:** Usando o ingress bare metal na porta 80<br>

**srv/Dockerfile**
```
FROM python:3.8-alpine
WORKDIR /app
COPY requirements.txt .
RUN python -m pip install --upgrade pip && pip install -r requirements.txt
COPY . .
EXPOSE 5000
CMD gunicorn --bind 0.0.0.0:5000 app:app
```

**Docker Hub - [giozandonai](https://hub.docker.com/u/giozandonai)**

**Criando a imagem sem o compose:** `$ docker build -t giozandonai/conversao-distancia:v1 .`

**Enviando imagem:** `$ docker push giozandonai/conversao-distancia:v1`

**Adicionando tag latest:** `$ docker tag giozandonai/conversao-distancia:v1 conversao-distancia:latest`

**Enviando imagem:**
`$ docker push giozandonai/conversao-distancia:latest`

## DOCKER COMPOSE

**Rodando com o compose:**
`$ docker-compose up -d`

**Rodando com o Docker run:**
`$ docker container run -d --name conversao-distancia -p 5000:5000 giozandonai/conversao-distancia:v1`

**Acessando a aplicação:**
`http://localhost:5000`

## KUBERNETES

Acessar a pasta ./k8s:

`kubectl apply -f . -R`

`http://nome_dominio`
