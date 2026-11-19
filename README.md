# Prova2-Computa-o-em-Nuvem

Questão 1 -

A principal diferença entre SaaS e IaaS está no nível de gerenciamento e controle: o SaaS entrega um software pronto para uso via internet, enquanto o IaaS entrega a infraestrutura bruta (servidores, rede e armazenamento) para você configurar e administrar.

Questão 2 -
Uma empresa utiliza servidores próprios e também recursos de um provedor de nuvem pública. Qual modelo de emplantação em nuvem essa empresa utiliza?
Essa empresa utiliza o serviço de nuvem híbrida.

Questão 3 -
Qual a principal diferença entre uma máquina virtual e um contêiner?
uma máquina virtual (VM) virtualiza o hardware e roda seu próprio sistema operacional completo, enquanto um contêiner virtualiza o sistema operacional e compartilha o kernel do sistema hospedeiro (host)


Evidência 1 Contêiner em execução  
root@ubuntu:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

Evidencia 1 - container em execução
root@controlplane:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

Evidencia 2 - Página personalizada
root@controlplane:~/meu-nginx$ curl http://localhost:8080
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Meu servidor Nginx</title>
    <style>
        body {
            background-color: #202b38;
            color: white;
            font-family: Arial;
            text-align: center;
            padding-top: 100px;
        }
        h1 {
            color: #00ff99;
            font-size: 40px;
        }

        p {
            font-size: 20px;
        }
    </style>
</head>
<body>

<h1>Oi, eu sou o ELYWELTON FERREIRA NUNES!</h1>

    <p>Servidor web utilizando Nginx e Docker.</p>

    <p>Servidor rodando</p>

</body>
</html>
root@controlplane:~/meu-nginx$

Evidencia 3 - Deployment e Pod
root@controlplane:~/meu-nginx$ kubectl get deployments
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
meu-nginx   2/2     2            2           21s
root@controlplane:~/meu-nginx$ kubectl get pods
NAME                         READY   STATUS    RESTARTS   AGE
meu-nginx-664dc46b97-6fnqn   1/1     Running   0          57s
meu-nginx-664dc46b97-wmdf4   1/1     Running   0          57s
root@controlplane:~/meu-nginx$ kubectl get rs
NAME                   DESIRED   CURRENT   READY   AGE
meu-nginx-664dc46b97   2         2         2       70s

Evidencia 4 - Escalabilidade
root@controlplane:~/meu-nginx$ kubectl scale deployment meu-nginx --replicas=3
deployment.apps/meu-nginx scaled
root@controlplane:~/meu-nginx$ kubectl get pods
NAME                         READY   STATUS    RESTARTS   AGE
meu-nginx-664dc46b97-2dmlf   1/1     Running   0          16s
meu-nginx-664dc46b97-6fnqn   1/1     Running   0          3m48s
meu-nginx-664dc46b97-wmdf4   1/1     Running   0          3m48s

Evidencia 5 = Autorrecuperação
root@controlplane:~/meu-nginx$ kubectl delete pod meu-nginx-664dc46b97-6fnqn
pod "meu-nginx-664dc46b97-6fnqn" deleted from default namespace
root@controlplane:~/meu-nginx$ kubectl get pods
NAME                         READY   STATUS    RESTARTS   AGE
meu-nginx-664dc46b97-2dmlf   1/1     Running   0          2m52s
meu-nginx-664dc46b97-w5sgt   1/1     Running   0          16s
meu-nginx-664dc46b97-wmdf4   1/1     Running   0          6m24s

Evidencia 6 = Service e acesso HTTP
root@controlplane:~/meu-nginx$ kubectl get services
NAME         TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   13d

root@controlplane:~/meu-nginx$ kubectl run teste --image=curlimages/curl --rm -it --restart=never -- curl http://meu-nginx-service
error: invalid restart policy: never, valid values are: Always, OnFailure, Never

6 = Interpretação dos resultados
Questão 1 = Qual é a diferença entre uma imagem Docker e um contêiner em execução?
Uma imagem Docker é um modelo estático e somente leitura com o código, dependências e configurações da aplicação, enquanto um contêiner em execução é uma instância ativa e mutável dessa imagem rodando no sistema.

Questão 2 = Qual é a função de um deployment no Kubernetes?
Deployment gerencia de forma declarativa o ciclo de vida de aplicações executadas em Pods, garantindo o estado desejado do cluster. Ele atua uma camada acima do ReplicaSet, controlando a criação, escalabilidade e atualização das instâncias.

Questão 3 = O que aconteceu quando você excluiu um pod? Por que isso aconteceu?
O pod foi substituido logo que foi deletado por um pod novo.

Questão 4 = Qual é a finalidade de um service no kubernetes?
Fornece um ponto de rede estável (IP virtual e nome DNS) para acessar um conjunto de Pods que mudam de endereço ao serem criados, escalados ou substituídos.







 
