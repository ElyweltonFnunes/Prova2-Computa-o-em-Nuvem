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





 
