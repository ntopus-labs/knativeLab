REQUERIDO
kubernetes 1.22 ou mais

k3d cluster create testknative --k3s-arg "--disable=traefik@server:0"
kubectl apply -f https://github.com/knative/operator/releases/download/knative-v1.4.0/operator.yaml
kubectl get deployment knative-operator
    coloca coisas dentro do operator pra rodar
kubectl apply -f custom.yaml
kubectl --namespace knative-serving get service kourier
kubectl apply -f https://github.com/knative/serving/releases/download/knative-v1.4.0/serving-default-domain.yaml
docker build -t helloworld-go .

* Knative escalou devido a necessidade pra cima, ele escala pra baixo também?
* wrk fazer um artigo simples

* mais dificil pra subir, mas mais robusto e simples de codar
    * tem integração de eventos

wrk
hey -z 30s -c 50 "http://hello.default.172.20.0.2.sslip.io/" && kubectl get pods

pra chegar no operator vc tem que ta muito maduro
quem é Kourier?
custom resource cria um bagulho tipo um pod dá pra fazer get 

tá velho mas tá organizado
https://github.com/andrewwebber/learn-knative

codar mais em eventos