# ZappComments-meta

# 📝 ZappComments - Microsserviços com Spring Boot

Este repositório contém a implementação do sistema **ZappComments**, desenvolvido como parte de um desafio técnico com foco em microsserviços e comunicação síncrona utilizando **Spring Boot + RestClient**. O objetivo principal é permitir o envio de comentários por usuários e sua moderação automática com base em uma lista de palavras proibidas.

## 🔍 Visão Geral

O sistema é dividido em dois microsserviços:

- **CommentService:** responsável por expor a API pública de comentários, armazenar apenas os aprovados e se comunicar com o serviço de moderação.
- **ModerationService:** responsável por validar o conteúdo do comentário com base em uma lista de palavras proibidas.

A comunicação entre os serviços é feita de forma síncrona via HTTP, com tratamento de falhas e timeouts devidamente configurados.

## 🚀 Funcionalidades

- ✅ Criar novo comentário
- 🔎 Consultar comentário aprovado por ID
- 📄 Listar comentários aprovados com paginação
- 🛡️ Moderação automática contra palavras ofensivas

## 📦 Estrutura de Endpoints

### CommentService

| Método | Endpoint              | Descrição                            |
|--------|-----------------------|--------------------------------------|
| POST   | `/api/comments`       | Criação de novo comentário           |
| GET    | `/api/comments/{id}`  | Consultar comentário aprovado por ID |
| GET    | `/api/comments`       | Listar comentários aprovados         |
| DELETE | `/api/comments/{id}`  | Deleta um comentário                 |

### ModerationService

| Método | Endpoint         | Descrição                              |
|--------|------------------|----------------------------------------|
| POST   | `/api/moderate`  | Moderação de texto do comentário       |

## 🔐 Regras de Negócio

- Comentários com palavras proibidas como `"ódio"` , `"xingamento"` ou `"palavrões"` são rejeitados.
- Apenas comentários aprovados são persistidos.
- Chamadas entre os serviços têm timeout de 5 segundos.
- Respostas seguem os códigos HTTP corretos (201, 404, 422, 502, 504, etc).

## 🧪 Testes Realizados

- ✅ Comentário válido
- ❌ Comentário com palavras proibidas
- ⏱️ Simulação de timeout no serviço de moderação
- 🔍 Busca por comentário inexistente

## 🛠 Tecnologias Utilizadas

- Java 17+
- Spring Boot 3
- Spring Web / RestClient
- H2 Database (persistência em memória)
- Maven
- Postman (testes manuais)

## 📂 Postman Collection

Você pode importar a collection no Postman para testar todos os endpoints facilmente:

📥 [Download da Collection](./postman/AlgaComments.postman_collection.json)

> A pasta `postman/` contém a collection e ambientes configurados.

## 💡 Considerações Finais

Este projeto foi uma excelente oportunidade para aplicar boas práticas de microsserviços, timeout controlado, tratamento de erros e comunicação entre sistemas de forma síncrona proposto pela **Algaworks**.

---

Feito por Thiago Zappiello

