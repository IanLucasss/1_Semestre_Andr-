# Projeto de Banco de Dados - Biblioteca 📚

## Autores
- Ian Lucas  
- Juan Correa  
- Caroline Almeida  
- Matheus Pulcinelli  

## DDL - Data Definition Language

```sql
CREATE TABLE Cliente (
    id_cliente INT PRIMARY KEY,
    nome_cliente VARCHAR(50),
    cpf_cliente VARCHAR(11),
    email_cliente VARCHAR(50),
    telefone_cliente VARCHAR(11),
    endereco_cliente VARCHAR(100),
    data_nascimento DATE,
    data_cadastro DATE
);

CREATE TABLE Funcionario (
    id_funcionario INT PRIMARY KEY,
    nome_funcionario VARCHAR(255) NOT NULL,
    cpf_funcionario VARCHAR(20) NOT NULL UNIQUE,
    cargo VARCHAR(100) NOT NULL,
    telefone_funcionario VARCHAR(20)
);

CREATE TABLE Produto (
    id_produto INT PRIMARY KEY,
    nome_produto VARCHAR(255) NOT NULL,
    descricao TEXT,
    preco DECIMAL(10, 2) NOT NULL,
    categoria VARCHAR(100)
);

CREATE TABLE Genero (
    id_genero INT PRIMARY KEY,
    nome VARCHAR(50) NOT NULL UNIQUE,
    descricao TEXT
);

CREATE TABLE Livro (
    id_livro INT PRIMARY KEY,
    id_produto INT NOT NULL,
    nome_livro VARCHAR(100) NOT NULL,
    autor VARCHAR(100),
    editora VARCHAR(100),
    ano_publicacao INT,
    num_paginas INT,
    descricao VARCHAR(255),
    id_genero INT,
    FOREIGN KEY (id_produto) REFERENCES Produto(id_produto),
    FOREIGN KEY (id_genero) REFERENCES Genero(id_genero)
);

CREATE TABLE Estoque (
    id_estoque INT PRIMARY KEY,
    id_produto INT NOT NULL,
    quantidade INT NOT NULL DEFAULT 0,
    localizacao VARCHAR(100),
    FOREIGN KEY (id_produto) REFERENCES Produto(id_produto)
);

CREATE TABLE Pedido (
    id_pedido SERIAL PRIMARY KEY,
    id_cliente INT NOT NULL,
    id_funcionario INT,
    data_pedido DATE NOT NULL,
    status VARCHAR(50) NOT NULL,   
    total DECIMAL(10, 2) NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Cliente(id_cliente),
    FOREIGN KEY (id_funcionario) REFERENCES Funcionario(id_funcionario)
);

CREATE TABLE Emprestimo (
    id_emprestimo INT PRIMARY KEY,
    id_cliente INT NOT NULL,
    id_produto INT NOT NULL,
    data_emprestimo DATE NOT NULL,
    data_devolucao DATE,
    status VARCHAR(100) NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Cliente(id_cliente),
    FOREIGN KEY (id_produto) REFERENCES Produto(id_produto)
);

CREATE TABLE Contrato (
    id_contrato INT PRIMARY KEY,
    id_cliente INT NOT NULL,
    tipo_contrato VARCHAR(50),
    data_inicio DATE NOT NULL,
    data_fim DATE,
    valor DECIMAL(10, 2) NOT NULL,
    termos TEXT,
    FOREIGN KEY (id_cliente) REFERENCES Cliente(id_cliente)
);
```

---

## DML - Data Manipulation Language

```sql
-- Inserção
INSERT INTO Cliente VALUES (1, 'Maria Silva', '12345678901', 'maria@email.com', '11999999999', 'Rua das Flores, 45', '1990-05-15', CURRENT_DATE);

-- Atualização
UPDATE Cliente SET email_cliente = 'maria.silva@email.com' WHERE id_cliente = 1;

-- Exclusão
DELETE FROM Cliente WHERE id_cliente = 1;
```

---

## DQL - Data Query Language

```sql
-- Listar todos os clientes
SELECT * FROM Cliente;

-- Produtos disponíveis em estoque
SELECT p.nome_produto, e.quantidade
FROM Produto p
JOIN Estoque e ON p.id_produto = e.id_produto
WHERE e.quantidade > 0;

-- Consulta de livros e gêneros
SELECT l.nome_livro, g.nome AS genero
FROM Livro l
JOIN Genero g ON l.id_genero = g.id_genero;

-- Empréstimos em andamento
SELECT e.id_emprestimo, c.nome_cliente, p.nome_produto, e.data_emprestimo, e.status
FROM Emprestimo e
JOIN Cliente c ON e.id_cliente = c.id_cliente
JOIN Produto p ON e.id_produto = p.id_produto
WHERE e.status = 'Em andamento';
```

---

## DCL - Data Control Language

```sql
-- Criação de usuários
CREATE USER colaborador_biblioteca WITH PASSWORD 'senha123';
CREATE USER visitante_biblioteca WITH PASSWORD 'senha123';

-- Concessão de privilégios
GRANT SELECT, INSERT, UPDATE ON Cliente TO colaborador_biblioteca;
GRANT SELECT ON Produto, Livro, Genero TO visitante_biblioteca;

-- Revogação de permissões
REVOKE INSERT, UPDATE ON Produto FROM colaborador_biblioteca;
```

---

## 📁 Estrutura Baseada nos Arquivos Excel
Ver arquivo `Tabelas - BD.xlsx` para visualização e preenchimento inicial de dados de exemplo.
