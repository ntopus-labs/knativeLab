## TODO - Apontar as necessidades de instalação
instalar o wrk

REQUERIDO
kubernetes 1.22 ou mais
```
k3d cluster create testknative --k3s-arg "--disable=traefik@server:0"
kubectl apply -f https://github.com/knative/operator/releases/download/knative-v1.6.0/operator.yaml
kubectl config set-context --current --namespace=default

kubectl get deployment knative-operator
    coloca coisas dentro do operator pra rodar
kubectl apply -f custom.yaml
kubectl --namespace knative-serving get service kourier
kubectl apply -f https://github.com/knative/serving/releases/download/knative-v1.6.0/serving-default-domain.yaml
docker build -t localhost:5000/helloworld-go:latest .
k3d image import localhost:5000/helloworld-go:latest -c testknative
kubectl apply -f service.yaml

kubectl get ksvc helloworld-go  --output=custom-columns=NAME:.metadata.name,URL:.status.url
```

* Knative escalou devido a necessidade pra cima, ele escala pqra baixo também?
* wrk fazer um artigo simples

* mais dificil pra subir, mas mais robusto e simples de codar
    * tem integração de eventos

## Validação de benchmark

https://github.com/rakyll/hey
```
./hey -z 30s -n 1600 -c 600 "http://hello.default.172.20.0.2.sslip.io/"
```

pra chegar no operator vc tem que ta muito maduro
quem é Kourier?
custom resource cria um bagulho tipo um pod dá pra fazer get 

tá velho mas tá organizado
https://github.com/andrewwebber/learn-knative

## TroubleShooting 
* Caso o knative esteja dando problema com o traefik do k3d é necessário setar o "--disable=traefik@server:0" ao criar o cluster, conforme utilizado no exemplo
* Dando o kubectl get pods não vai ser encontrado a função que subiu, para encontrar é necessário procurar por kubectl get ksvc