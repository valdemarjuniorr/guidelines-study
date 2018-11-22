# Estudo sobre kubernetes
Guia criado basedo em estudos sobre kubernetes.

## Convenções usadas neste documento
As palavras-chave de nível de exigência **"PRECISA"**, **"NÃO PRECISA"**, **"OBRIGATÓRIO"**, **"DEVERÁ"**, **"NÃO DEVERÁ"**, **"DEVE"**, **"NÃO DEVE"**, **"RECOMENDADO"**, **"PODE"** e **"OPCIONAL"** usadas serão interpretadas conforme descrito no RFC 2119.

## Kubernete
Kubernete é um orquestrador de containers Docker.

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

### Executar uma imagem dentro do cluter
`kubectl run [NOME_EXPOSTO] --image=[IMAGEM] [--port=PORTA]`
Ex.: kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.4 --port=8080

### Expôr um container 
kubectl expose deployment [--port=PORTA] [--name=NOME] [--external-ip=external-ip-of-service] [--type=type] [--target-port=number-or-name] [options]

Ex.: kubectl expose deployment hello-minikube --type=NodePort
Ex.2: kubectl expose deployment nginx --port=80 --target-port=8000
