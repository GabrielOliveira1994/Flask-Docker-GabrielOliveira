Meus Primeiros Passos com Docker — Trabalho RASI

Aluno(a): [Seu Nome Completo]

Disciplina: Redes e Administração de Sistemas (RASI)

Professor: Cesar Augusto de Moraes Costa

Curso: Técnico em Informática Integrado ao Ensino Médio — IFSP Campus Campos do Jordão

Objetivo

Este repositório documenta meus primeiros passos na criação de uma máquina virtual com Ubuntu Server, configuração de acesso remoto via SSH e containerização de uma aplicação Flask utilizando Docker.

O que foi feito

1. Infraestrutura (VM e SSH)

Criei uma máquina virtual no VirtualBox com Ubuntu Server.

Configurei a placa de rede da VM no modo NAT.

Descobri o endereço IP da VM com hostname -I.

Conectei via SSH a partir do terminal da máquina hospedeira:

ssh aluno@IP_DA_VM


2. Primeiros passos com Docker

Verifiquei a instalação do Docker com os comandos:

docker --version
docker run hello-world


O comando docker run hello-world baixa uma imagem mínima e confirma que o Docker está funcionando corretamente.

3. Containerização de uma aplicação Flask

Criei uma aplicação simples em Flask e a containerizei usando a imagem base python:3.14-slim.

Dockerfile utilizado:

FROM python:3.14-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY app.py .
EXPOSE 5000
CMD ["python", "app.py"]


Construí e executei o container com:

docker build -t flask-app .
docker run -d -p 5000:5000 --name meu-flask flask-app


4. Expansão da aplicação

Adicionei novas rotas (/sobre e /contato) com layouts visuais diferentes, e reconstruí a imagem para testar as mudanças.

Principais aprendizados

[Escreva aqui 2-3 frases sobre o que você achou mais interessante ou desafiador — por exemplo, a diferença entre modo Bridge e NAT, ou como o Docker isola o ambiente da aplicação.]

Referência

Repositório base fornecido pelo professor: CesarAugusto88/RAS-Docker
