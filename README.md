# Kube-News

Uma aplicação para site de notícias desenvolvida por [Fabrício Veronez](https://github.com/fabricioveronez) no curso [Formação Devops PRO 2.0](https://curso.devopspro.com.br/devops-pro/), feita em NodeJS para demonstrar o uso de containers.

## 📋 Sobre o Projeto

O projeto Kube-News é uma aplicação web simples desenvolvida em Node.js, projetada como exemplo para demonstrar o uso de contêineres. É um portal de notícias que permite criar, visualizar e gerenciar artigos através de uma interface web. 
Toda estrutura do site foi disponibilizada para os alunos do curso Formação Devops PRO 2.0, e o objetivo proposto foi criarmos toda infraestrutura para hospedar o site utilizando o Docker como base.

### 🚀 Funcionalidades Principais

- Listagem de notícias na página inicial
- Criação de novas notícias através de formulário
- Visualização detalhada de cada notícia
- Endpoints de health check para monitoramento

## 🛠️ Tecnologias Utilizadas

- **Backend**: Node.js com Express.js
- **Frontend**: EJS (Embedded JavaScript) como motor de templates
- **Banco de Dados**: PostgreSQL com Sequelize ORM

## Estrutura de Arquivos

- Dockerfile
   - Cria uma imagem otimizada para execução da aplicação utilizando tecnologias como multistage build e melhores práticas garantindo a eficiência do serviço.
- compose.yaml
   - Cria os containers necessários para subir toda a aplicação

### Pré-requisitos

- Docker (Para containerização)
- Kubernetes (opcional, para orquestração)

### Variáveis de Ambiente

Para configurar a aplicação, defina as seguintes variáveis de ambiente:

| Variável | Descrição | Valor Padrão |
|----------|-----------|--------------|
| DB_DATABASE | Nome do banco de dados | kubedevnews |
| DB_USERNAME | Usuário do banco de dados | kubedevnews |
| DB_PASSWORD | Senha do usuário | Pg#123 |
| DB_HOST | Endereço do banco de dados | localhost |
| DB_PORT | Porta do banco de dados | 5432 |
| DB_SSL_REQUIRE | Habilitar SSL para conexão | false |

## 🚀 Instalação e Execução

### Execução Local

1. Faça o clone do repositório
2. Configure as variáveis de ambiente necessárias
3. Inicie a aplicação utilizando o Docker Compose com o terminal no diretório do arquivo "compose.yaml":
   ```bash
   docker compose up -d --build
   ```
5. Acesse a aplicação em [http://localhost:8080](http://localhost:8080)

## 📊 Monitoramento e Health Checks

A aplicação disponibiliza endpoints para monitoramento e também recursos para simular cenários de falha, muito úteis para testar a resiliência em ambientes Kubernetes:

## 🔒 Modelo de Dados

O projeto utiliza um único modelo `Post` com os seguintes campos:

| Campo | Tipo | Descrição |
|-------|------|-----------|
| title | String | Título da notícia (limite: 30 caracteres) |
| summary | String | Resumo da notícia (limite: 50 caracteres) |
| content | String | Conteúdo completo (limite: 2000 caracteres) |
| publishDate | Date | Data de publicação |


