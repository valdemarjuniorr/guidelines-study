# Estudo sobre Docker
Guia criado basedo em estudos de Docker.

## Convenções usadas neste documento
As palavras-chave de nível de exigência **"PRECISA"**, **"NÃO PRECISA"**, **"OBRIGATÓRIO"**, **"DEVERÁ"**, **"NÃO DEVERÁ"**, **"DEVE"**, **"NÃO DEVE"**, **"RECOMENDADO"**, **"PODE"** e **"OPCIONAL"** usadas serão interpretadas conforme descrito no RFC 2119.

## Docker
Docker é uma tecnologia de software que fornece contêineres, promovido pela empresa Docker, Inc. O Docker fornece uma camada adicional de abstração e automação de virtualização de nível de sistema operacional no Windows e no Linux. Fonte: [Wikipédia](https://pt.wikipedia.org/wiki/Docker_(software))

## Comandos

### Containers

### Criar
`docker [container] run [-d --detach] [--name (NOME)] [-e ou --env (VARIÁVEL DE AMBIENTES)] (NOME_CONTAINER)`
Ex.:docker [container] run --publish 80:80 -d --name nginx nginx

### Excluir
`docker [container] rm [-f] (NOME/ID CONTAINER)`

### Criar, executar comando e excluir
- `docker container run -rm -it ubuntu bash`
- `docker container start -ai (NOME_CONTAINER)`. Faz a mesma coisa do `docker container run`, mas para um container existente.

### Ver logs
`docker logs [--tail 50] (NOME/ID CONTAINER)`

### Listar
`docker container ls [-a]`

### Verificar processos rodando dentro do container
- `docker container top (NOME_CONTAINER)`
- `docker container inspect (NOME_CONTAINER)`
- `docker container stats (NOME_CONTAINER)`

### Ter o shell dentro do container
`docker container run -it (NOME_CONTAINER) bash`

Obs.: Irá criar um novo container.

### Entra no Shell do container em execução
`docker container exec -it (NOME_CONTAINER) bash`

## Rede/NetWork

### Lista as redes criadas
`docker network ls`

### Listar detalhes
`docker network inspect (NOME_DA_REDE)`

### Criar
`docker network create (NOME_DA_REDE)`

### Usar uma rede específica
`docker container run -d [--name (NOME_CONTAINER)] --network (NOME_DA_REDE) (NOME_CONTAINER)`

### Conectar um container de uma rede
`docker network connect (NOME_DA_REDE) (NOME_CONTAINER)`

### Desconectar um container de uma rede
`docker network disconnect (NOME_DA_REDE) (NOME_CONTAINER)`

## Imagens

### Listar
`docker image ls`

### Inspecionar uma imagem
`docker image inspect (NOME_IMAGE)`

### Verificar o que histórico de uma imagem
`docker history (NOME_IMAGE)`

### Download a imagem do dockerhub
`docker pull (NOME_DA_IMAGEM)`

### Criar uma tag
`docker image tag nginx valdemarjuniorr/nginx`

### Logar no dockerhub
`docker login [-u (NOME_USUARIO_DOCKERHUB)]`

### Construir uma imagem a partir de um Dockerfile
`docker image build -t customnginx .`

### Upload uma imagem para o dockerhub
`docker image push valdemarjuniorr/nginx`
