# Estudo sobre kubernetes
Guia criado basedo em estudos sobre kubernetes.

## Convenções usadas neste documento
As palavras-chave de nível de exigência **"PRECISA"**, **"NÃO PRECISA"**, **"OBRIGATÓRIO"**, **"DEVERÁ"**, **"NÃO DEVERÁ"**, **"DEVE"**, **"NÃO DEVE"**, **"RECOMENDADO"**, **"PODE"** e **"OPCIONAL"** usadas serão interpretadas conforme descrito no RFC 2119.

## Kubernete
Kubernete é um orquestrador de containers Docker.

## Dockerfile
É o arquivo usado para criação automática images Docker. Exemplo do (kuard(Kubernetes up and running))[https://github.com/kubernetes-up-and-running/kuard].
```
FROM alpine
MAINTAINER Valdemar jr <valdemarjuniorr@gmail.com>
COPY bin/kuard /kuard
ENTRYPOINT ["/kuard"]
```
Então executar o seguinte comando `docker build -t kuard-amd64:1 .`.


## Instalação
- [minikube]()
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads) ou [KVM](https://github.com/kubernetes/minikube/blob/master/docs/drivers.md#kvm-driver)

OBS.: Caso tenha algum problema ao instalar VirtualBox, [veja aqui](https://www.if-not-true-then-false.com/2010/install-virtualbox-with-yum-on-fedora-centos-red-hat-rhel/)

## Comandos

## Minikube
Sobre o [minikube](https://github.com/kubernetes/minikube)

### Iniciar minikube
`minikube start`

### Abrir dashboard
`minikube dashboard`

### Acessar serviço
Para acessar um serviço exposto via _node port_, execute:
`minikube service [-n NOME_EXPOSTO] [--url] NOME`

### Executar uma imagem dentro do cluster
`kubectl 0 [NOME_EXPOSTO] --image=[IMAGEM] [--port=PORTA]`
Ex.: kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.4 --port=8080

### Expôr um container 
kubectl expose deployment [--port=PORTA] [--name=NOME] [--external-ip=external-ip-of-service] [--type=type] [--target-port=number-or-name] [options]

Ex.: kubectl expose deployment hello-minikube --type=NodePort
Ex.2: kubectl expose deployment nginx --port=80 --target-port=8000

### Criar Pod
O arquivo `helloworld.yml` poderia estar dentro do projeto ou dentro de um repositório separado do projeto para ser executado e criado dentro do kubernetes.
`kubectl create -f helloworld.yml`.

### Listar Pods
`kubectl get pod`.

### Detalhar Pod
`kubectl describe pod NOME`.

### Redirecionar uma porta local para uma porta dentro do container
O comando irá dispobibilizar localmente acesso a porta `8081` que será direcionada para a a porta `3000` dentro do kubernetes.
`kubectl port-forward NOME 8081:3000`.

### Executar comando dentro do container
`kubectl exec NOME -- COMANDO`.
Ex.: kubectl exec activego-db -- ls /app 