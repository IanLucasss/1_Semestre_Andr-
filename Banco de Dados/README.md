# Projeto Final: Banco de Dados Relacional

## Objetivo

Este repositório contém o projeto final da disciplina de Banco de Dados Relacional. O objetivo foi desenvolver um **Sistema de Gerenciamento de Biblioteca**, aplicando os conceitos de modelagem conceitual, lógica e física, além da normalização e manipulação de dados com DDL, DML, DQL e DCL.

## Integrantes do Grupo

- Ian Lucas
- Juan Correa
- Caroline Almeida
- Matheus Pulcinelli

## Tema Escolhido

> _Sistema de Gerenciamento de Biblioteca_

O projeto visa permitir o controle de clientes, funcionários, livros, empréstimos, contratos, estoque e pedidos de uma biblioteca, garantindo integridade, segurança e organização no gerenciamento de dados.

## Modelagem de Dados

### Entidades, Atributos e Relacionamentos

O sistema foi modelado com as seguintes entidades principais:

- **Cliente:** Cadastro de usuários da biblioteca.
- **Produto:** Itens disponíveis na biblioteca (livros, periódicos, etc.).
- **Livro:** Especialização de Produto.
- **Gênero:** Classificação dos livros.
- **Estoque:** Controle de quantidade e localização dos produtos.
- **Pedido:** Registro de solicitações feitas pelos clientes.
- **Empréstimo:** Controle de empréstimos de produtos.
- **Contrato:** Acordos firmados com clientes.
- **Funcionário:** Cadastro de colaboradores.

### Diagrama Entidade-Relacionamento (DER)

> Link para o DER:  
[DER no Miro](https://miro.com/app/board/uXjVImkHCvA=/)


## Normalização

O banco de dados foi normalizado até a **Terceira Forma Normal (3FN)**.

- **1FN:** Eliminação de grupos repetitivos e uso de atributos atômicos.
- **2FN:** Garantia de dependência completa da chave primária.
- **3FN:** Eliminação de dependências transitivas.

### Justificativas:

A normalização foi aplicada para minimizar redundâncias, garantir integridade e facilitar a manutenção futura.

## Scripts SQL

### DDL (Data Definition Language)

- Criação de tabelas
- Definição de chaves primárias e estrangeiras
- Restrições de integridade


### DML (Data Manipulation Language)

- Inserção de dados (ex.: Cliente, Produto, Gênero)
- Atualização de registros
- Exclusão de registros


### DQL (Data Query Language)

- Consultas de clientes, estoque, livros por gênero e empréstimos em andamento.


### DCL (Data Control Language)

- Criação de usuários
- Concessão e revogação de permissões


### DTL (Data Transaction Language)

> Não implementado neste projeto.

## Documentação (ABNT)

- Introdução
- Modelagem conceitual e lógica
- Scripts comentados
- Conclusão e referências


## Requisitos Técnicos

- **SGBD utilizado:** PostgreSQL
- **Versão recomendada:** PostgreSQL 15+
- **Ferramentas utilizadas:**
  - PgAdmin
  - DBeaver
  - VSCode

---

## Observações Finais

Este projeto serviu como base prática para a aplicação dos conceitos aprendidos na disciplina de Banco de Dados.
